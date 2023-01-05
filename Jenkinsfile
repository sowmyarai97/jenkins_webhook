pipeline {
    agent any
    environment{
        GLOBAL_VAR ='5'
        artifact_password=credentials('artifact-secret')
    }
    parameters {
        booleanParam(name: "TEST_BOOLEAN", defaultValue: true, description: "Sample boolean parameter")
    }
    stages {
        stage('predefined variables') {
            steps {
               sh 'env | sort'
               echo "$BUILD_NUMBER"
            }
        }
        stage('global variables') {
            when {
                expression { params.booleanParam == "true" }
            }
            steps {
                echo "$GLOBAL_VAR"
                echo "$artifact_password"
                echo "$firstname"
            }
        }    
        stage('stage defined variable') {
            environment{
                STAGE_VAR ='8'
            } 
            steps {
                echo "$STAGE_VAR"
            }
        }  
        stage('All variables') {
            steps {
                echo "$GLOBAL_VAR"
                echo "$defined_global_var"
            }
        }    
    }
} 
##testing
