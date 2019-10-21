# Jenkins Libs

## Git tag and push
```groovy
def call(Map config) {

	def tag = config.tag
	def commit = config.commit

	println "Tagging commit ${commit} with tag ${tag}"

	try {
		tag_exists = sh (
		    script: "git tag -l ${tag}",
		    returnStdout: true
		).trim()

		if ( tag_exists ) {
		    error 'Tag already exists. Be careful of modifying your project version in VERSION file of your project.'
		}

		withCredentials([sshUserPrivateKey(credentialsId: 'gitlab-ssh-key', keyFileVariable: 'SSH_KEY')]) {
		    withEnv(["GIT_SSH_COMMAND=ssh -i $SSH_KEY -o StrictHostKeyChecking=no"]) {
			sh """
			    git tag -a ${tag} -m '[RELEASE] This tag has been created by Jenkins server' ${commit}
			    git push origin ${tag}
			"""
		    }
		}

	} finally {
		println "Finally"
	}
}
```
