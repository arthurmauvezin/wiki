# Jenkinsfile

## Pipeline global configuration
### Keep only 5 last build
```groovy
pipeline {
    options {
        buildDiscarder(logRotator(numToKeepStr: '5', artifactNumToKeepStr: '5'))
    }
}
```

### Trigger build every night
```groovy
pipeline {
    triggers {
      cron '0 0 * * *'
    }
}
```

### Set environment variables
Following example allows you to get Git short hash and commiter name alongside project version (from a VERSION file)
```groovy
pipeline {
    environment {
        GIT_SHORT_HASH = "${env.GIT_COMMIT.substring(0,8)}"
        GIT_LAST_COMMITTER_NAME = """ ${sh(
                returnStdout: true,
                script: 'git show -s --pretty=%an'
            )}"""
        RELEASE_VERSION = readFile('VERSION').trim()
        COMMIT_VERSION = "${env.RELEASE_VERSION}-${env.GIT_SHORT_HASH}"
    }
```

## Use login password credentials in stage
### Login/password credentials
```groovy
stage('My stage') {
    environment {
	APP_ACCESS_CREDS=credentials('credentials-app-credentials')
    }
    steps {
	sh "securecommand --username ${env.APP_ACCESS_CREDS_USR} --password ${env.APP_ACCESS_CREDS_PSW}"
    }
}
```
### Token credentials
```groovy
stage('My stage') {
    environment {
	APP_ACCESS_TOKEN=credentials('credentials-app-access-key')
    }
    steps {
	sh "securecommand --token ${env.APP_ACCESS_TOKEN} "
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

## Branch context
> `beforeAgent true` allows following conditions (branch) to be evaluvuated before agent creation.
```groovy
stage('My stage') {
    when {
        beforeAgent true
	anyOf {
	    branch 'master'
	    branch 'develop'
	}
    }
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

## Post Actions
### Slack 
```groovy
    post {
        success {
            slackSend channel: '#channel-name', color: 'good', message: "The pipeline ${currentBuild.fullDisplayName} completed successfully: ${currentBuild.absoluteUrl}"
        }
        failure {
            script {
                def attachments = [
                    [
                        fallback: "The pipeline ${currentBuild.fullDisplayName} has failed",
                        color: 'danger',
                        author_name: "Last committer: ${env.GIT_LAST_COMMITTER_NAME}",
                        title: "The pipeline ${currentBuild.fullDisplayName} has failed",
                        title_link: "${currentBuild.absoluteUrl}",
                        text: "Click on title above to view build logs"
                    ]
                ]
                slackSend(channel: '#channel-name', attachments: attachments)
            }
        }
    }
```

