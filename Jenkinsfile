pipeline {
	agent any
	environment {
    	PATH = "/usr/lib/jvm/java-1.17.0-openjdk-amd64:${env.PATH}"
  	}
	stages {		
		stage ('Git SCM') {
			steps {
			git changelog: false, credentialsId: 'b44eb99c-187b-4d48-bbf4-a8cda78f4760', poll: false, url: 'git@github.com:Kapombo/online-shopping-system-advanced.git'
			}

		}
		stage ('Show PATH') {
			steps {
			 echo "PATH is: ${env.PATH}"
			}
		}
		stage ('CX Scan') {
			steps{
				checkmarxASTScanner additionalOptions: '--scan-types sca --project-tags scid:1234,5678',
				baseAuthUrl:'', 
				branchName:'', 
				checkmarxInstallation:'CLI', 
				credentialsId:'9937c97a-be69-4b33-a3d1-5547f4621ecf', 
				projectName:'Test_scan_Tags', 
				serverUrl:'https://cxst-qa.perf.cxast.net', 
				tenantName:'single-tenant-perf',
				useOwnAdditionalOptions: true,
                                useOwnServerCredentials: true
					}					
				}
	    stage("After pipeline") {
		    steps{
            		echo 'hello'
		    }
       	    }
	} //stages
}//pipeline
