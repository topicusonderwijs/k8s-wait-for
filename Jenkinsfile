config {
	daysToKeep = 21
	cronTrigger = '@weekend'
}

node() {
	catchError {
		git.checkout { }

		def img = dockerfile.build {
			name = 'groundnuty/k8s-wait-for'
		}

		dockerfile.publish {
			distribute = true
			image = img
			baseTag = false
		}
	}
	
	notify {
		slackChannel = 'jenkins-job-results'
	}
}
