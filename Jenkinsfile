pipeline {
agent any

environment {

dotnet='C:\\Program Files (x86)\\dotnet'
        NEXUS_VERSION = "nexus3"
        NEXUS_PROTOCOL = "http"
        NEXUS_URL = "localhost:8081"
        NEXUS_REPOSITORY = "nexus"
        NEXUS_CREDENTIAL_ID = "10d1819d-eb9f-4c82-b272-4ba1ab14ac49"

}
stages {
    stage('Checkout') {
        steps {
            git 'https://github.com/akhil690/DotNetCore22Console.git'
            
        }
        
    }
    stage('Restore') {
        steps {
            bat 'dotnet restore C:\\Windows\\system32\\config\\systemprofile\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\Lungs'
            }
        
    }
    stage('Clean') {
        steps {
            bat 'dotnet clean C:\\Windows\\system32\\config\\systemprofile\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\Lungs'
            
        }
        }
        stage('Build') {
            steps {
                bat 'dotnet build C:\\Windows\\system32\\config\\systemprofile\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\Lungs --configuration Release'
            
                }
            }
            stage('Unit Test') {
                steps {
                    bat 'dotnet test C:\\Windows\\system32\\config\\systemprofile\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\Lungs'
                    
                }
                
            }
            stage('Publish') {
                steps {
                    bat 'dotnet publish C:\\Windows\\system32\\config\\systemprofile\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\Lungs'
                    }
                
            }
        
            stage('Upload'){
                steps {
                    nexusArtifactUploader artifacts: [[artifactId: 'latest1.0.8', classifier: '', file: 'C:\\Windows\\System32\\config\\systemprofile\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\Lungs-Main\\dotnetcore22console\\bin\\Release\\netcoreapp2.2\\dotnetcore22console.dll', type: 'dll']], credentialsId: '10d1819d-eb9f-4c82-b272-4ba1ab14ac49', groupId: 'dotnet', nexusUrl: 'localhost:8081/', nexusVersion: 'nexus3', protocol: 'http', repository: 'nexusdot', version: '${BUILD_NUMBER}'
                
            }
}
}
}
