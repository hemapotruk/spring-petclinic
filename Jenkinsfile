node {
	def mavenHome
        
        stage('Code Checkout') { 
		// Get code from a repository and Git has to be installed in the system; git must be configured in the Global Tool Configuration
		git 'https://github.com/mitesh51/spring-petclinic.git'
           
		// Get the Maven tool configured in Global Tool Configuration 
		// 'apache-maven-3.5.3' Maven tool must be configured in the global configuration.
		mavenHome = tool 'maven3'
        }
    
	stage('Build') {
                // Execute shell script if OS flavor is Linux
                if (isUnix()) {
                        sh "'${mavenHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
                        // Publish JUnit Report
                        junit '**/target/surefire-reports/TEST-*.xml'
                } 
                else {
                        // Execute Batch script if OS flavor is Windows		
                        bat(/"${mavenHome}\bin\mvn" clean package/)
                        // Publish JUnit Report
                        junit '**/target/surefire-reports/TEST-*.xml'
                }
	}
}
