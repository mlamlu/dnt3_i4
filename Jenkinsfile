
/* *** Détail du projet, récupéré dans le pipeline en lisant le pom.xml *** */
def groupId = ''
def artefactId = ''
def filePath = ''
def packaging = ''
def version = ''
def verCode = UUID.randomUUID().toString()

pipeline {
    agent any

    tools {

    maven "maven_3_6_3"
    }


    environment {

        // This can be nexus3 or nexus2

        NEXUS_VERSION = "nexus3"
        // This can be http or https
        NEXUS_PROTOCOL = "http"
        // Where your Nexus is running
        NEXUS_URL = "localhost:8081"
        // Repository where we will upload the artifact
        NEXUS_REPOSITORY = "maven-snapshots"
        // Jenkins credential id to authenticate to Nexus OSS
        NEXUS_CREDENTIAL_ID = "nexus_localhost"
    }

    stages {


        stage('Package') {
            steps {
            	sh 'npm i'
            }
        }


        stage('test') {
            steps {
            	sh 'npm test'

            }
        }

        // stage('Analyse') {
        //     steps {
        //     	sh 'mvn checkstyle:checkstyle'
        //         sh 'mvn spotbugs:spotbugs'
        //         sh 'mvn pmd:pmd'
        //     }
        // }

//         stage('Publish') {
//             steps {
//                 archiveArtifacts 'target/*.jar'
//             }
//         }


//         stage("publish to nexus") {
//              steps {
//                  script {
//                                         pom = readMavenPom file: 'pom.xml'
//                                         groupId = pom.groupId
//                                         artifactId = pom.artifactId
//                                         packaging = pom.packaging
//                                         version = pom.version
//                                         filepath = "target/${artifactId}-${version}.jar"
//                   }
//                nexusPublisher nexusInstanceId: 'nexus_localhost', nexusRepositoryId: 'maven-releases', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: "${filepath}"]], mavenCoordinate: [artifactId: "${artifactId}", groupId: "${groupId}", packaging: "${packaging}", version: "${version}-${verCode}"]]]

//              }
//        }




//     }


//    post {
//       success {
//          junit '**/target/surefire-reports/*.xml'
//          archiveArtifacts '**/target/*.jar'
//          archiveArtifacts '**/target/*.xml'
//       }
//       always{
//         recordIssues enabledForFailure : true, tools: [mavenConsole(), java(), javaDoc()]
//         recordIssues enabledForFailure : true, tool: checkStyle()
//         recordIssues enabledForFailure : true, tool: pmdParser(pattern: '**/target/pmd.xml')
//         recordIssues enabledForFailure : true, tool: cpd(pattern: '**/target/cpd.xml')
//       }
//    }

}









/*     post {
            always {
                       junit '**//* surefire-reports *//*.xml'
                    }
         } */
