# Jenkinsfile

## Keep only 5 last build
```groovy
pipeline {
    options {
        buildDiscarder(logRotator(numToKeepStr: '5', artifactNumToKeepStr: '5'))
    }
}
```


## Trigger build every night
```groovy
pipeline {
    triggers {
      cron '0 0 * * *'
    }
}
```

## Use private registry to download docker agent
```groovy
agent {
    docker {
        image 'private-registry/my-image:0.1.2'
        registryUrl 'https://private-registry'
        registryCredentialsId 'registry-credentials-ro'
    }
}
```

## Use credentials in stage
```groovy
environment {
    APP_ACCESS_KEY=credentials('credentials-app-access-key')
}
```

## Stash and unstash changes
### Save changes in stash for later
```groovy
stash 'stash_name'
```
### Get back stash content in another stage
```groovy
unstash 'stash_name'
```

## Push git changes through ssh
```groovy
steps {
    withCredentials([sshUserPrivateKey(credentialsId: 'credentials-ssh-key', keyFileVariable: 'SSH_KEY')]) {
        withEnv(["GIT_SSH_COMMAND=ssh -i $SSH_KEY -o StrictHostKeyChecking=no"]) {
            sh """
            git checkout master
            echo "toto" >> dummy.txt
            git add dummy.txt
            git commit -m \"My commit message\" "
            git push origin master
            """
        }
    }
}

```

## Modify in one stage and push in another
```groovy
stages {
    stage('Build') {
        agent { label 'stage-1' }
        steps {
            sh "bash build.sh someting"
            stash 'git_changes'
        }
    }
    stage('Push to git') {
        agent { label 'stage-2' }
        steps {
            withCredentials([sshUserPrivateKey(credentialsId: 'jenkins-ssh-key', keyFileVariable: 'SSH_KEY')]) {
                withEnv(["GIT_SSH_COMMAND=ssh -i $SSH_KEY -o StrictHostKeyChecking=no"]) {
                    sh "git checkout master"
                    unstash 'git_changes'
                    sh """
                    git add .
                    git diff --staged --stat --name-only --no-color --quiet
                    if [ $? -eq 1 ]
                        git add CHANGELOG.md
                        git commit -m \"[AUTOMATIC] Backup \$(date +\"%d/%m/%Y %H:%M:%S\")\"
                        git push origin master
                    else
                        echo \"Nothing new to commit\"
                    fi
                    """
                }
            }
        }
    }
}

```
