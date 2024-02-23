pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''#!/bin/bash
                echo 'In C or Java, we can compile our program in this step.'
                echo 'In Python, we can build our package here or skip this step.'
                '''
            }
        }
        stage('Test') {
            steps {
                sh '''#!/bin/bash
                echo 'Test Step: We run testing tool like pytest here.'

                # Assuming Conda is installed and the path is known
                # Replace /path/to/conda with the actual path to your Conda executable
                export PATH=/path/to/conda/bin:$PATH
                
                # Initialize Conda in bash script
                eval "$(conda shell.bash hook)"

                # Activate the Conda environment
                conda activate <Environment_Name>

                # Run pytest or any other command you wish to run in your Conda environment
                # If pytest is not installed, ensure to install it within the environment first
                pytest <Additional_Commands_If_Any>

                # Note: No need to explicitly use `sudo` or `exit 1` here
                # Jenkins will mark the build as failed if any command returns a non-zero exit code
                '''

            }
        }
        stage('Deploy') {
            steps {
                echo 'In this step, we deploy our project.'
                echo 'Depending on the context, this may involve publishing the project artifact or uploading pickle files.'
            }
        }
    }
}
