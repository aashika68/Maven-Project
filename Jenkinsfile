node{
    stage("Checkout"){
    checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/kliakos/sparkjava-war-example.git']]])
    }
    
    stage ('Build') {

    git url: 'https://github.com/kliakos/sparkjava-war-example.git'

    withMaven(
        // Maven installation declared in the Jenkins "Global Tool Configuration"
        maven: 'Apache Maven 3.6.0',
        // Maven settings.xml file defined with the Jenkins Config File Provider Plugin
        // We recommend to define Maven settings.xml globally at the folder level using 
        // navigating to the folder configuration in the section "Pipeline Maven Configuration / Override global Maven configuration"
        // or globally to the entire master navigating to  "Manage Jenkins / Global Tools Configuration"
        mavenSettingsConfig: '13736e05-85bb-4715-8ec0-01b60e79a2fa') {

      // Run the maven build
      sh "mvn clean verify"

    } // withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe & FindBugs & SpotBugs reports...
  }
   
    
}
