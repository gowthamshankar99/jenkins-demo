pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                sh 'ls'
            }
        }
        
        stage('Build and Test') {
            steps {
                // Run your build and test commands here
                sh 'ls'
            }
        }
        stage('Validate CF Templates') {
            steps {
                script {
                    def templatesDir = ''  // assuming this is where the repo is cloned

                    // List all CloudFormation template files in the directory
                    def templateFiles = findFiles(glob: '**/*.json')

                    // Loop through each template file and validate
                    for (def templateFile in templateFiles) {
                        def templatePath = templateFile.path
                        echo "Validating template: ${templatePath}"

                        // Execute the AWS CLI command to validate the template
                        sh "aws cloudformation validate-template --template-body file://${templatePath}"
                    }
                }
            }
        }
    }
}
