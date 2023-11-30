pipeline {
	agent any
	environment {
    	PATH = "/usr/lib/jvm/java-1.8.0-openkdj-amd64:${env.PATH}"
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
				script{
					try {
						step([checkmarxASTScanner additionalOptions: '--project-tags SCID:12921,16225,17285,17729 --scan-types sast --file-filter !**/.git/**/*,!**/.gitgnore/**/*,!**/bin/**/*,!**/*.tmp,!**/*.gif,!**/*.jpg,!**/*.png,!**/*.exe,!**/*.dll,!**/*.jar,!**/*.launch,!Checkmarx/**/*,!OSADependencies.json,!**/node_modules/**/*,!**/.cxsca-results.json,!**/.cxsca-sast-results.json,!.checkmarx/**/*,!*/src/test/**/*,!*/archunit_store/**/*,!*/.settings/**/*,!*/.vscode/**/*,!**/*.spec.ts,!web/.storybook/**/*,!FinaceMigrations/**/*,!installer-parent/**/*,!installer-resources/**/*,!demo-*/**/*,!parent-test-server/**/*,!Tools/**/*,!web/tools/**/*,!server/build/**/*,!Finace/build/**/*,!server/licenses/**/*,!*test*/**/*,!**/testing/**/*,!web/.storybook/**/*,!**/*stories.mdx,!**/openapi-generator/**/*,!**/asciidoc/**/*,!**/*.jks,!**/*.jasper,!**/*.jrxml,!**/*.jrtx,!**/*.xsl*,!**/*.project,!**/*.classpath,!**/*.derived,!**/jenkins-common.groovy,!**/*.xpdl,!**/target/**/*,!**/test.ts,!**/src/test/**/* --report-format pdf --sca-exploitable-path false', baseAuthUrl: 'https://cxst-qa.perf.cxast.net', branchName: '', checkmarxInstallation: 'CLI', credentialsId: '9937c97a-be69-4b33-a3d1-5547f4621ecf', projectName: 'Test_scan_Tags', serverUrl: 'https://cxst-qa.perf.cxast.net', tenantName: 'single-tenant-perf'])
					}
					catch (Exception e) {
		
                       				 echo 'Checkmarx is currently unstable:'  
							//+ e.toString()
                        				//catchError(stageResult: 'UNSTABLE', buildResult: currentBuild.currentResult) {
                       					// error 'Checkmarx is unstable'
                       					// }
                       				currentBuild.result = 'UNSTABLE'
					}
				}
			}
		}
	    stage("After pipeline") {
		    steps{
            		echo 'hello'
		    }
       	    }
	} //stages
}//pipeline
