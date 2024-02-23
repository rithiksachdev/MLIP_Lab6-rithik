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
                # Check if the virtual environment already exists
                
                echo 'Creating a virtual environment.'
                python3 -m venv mlip
                source mlip/bin/activate
                echo 'Installing dependencies.'
                pip install -r requirements.txt
                

                # Run pytest
                pytest

                # Deactivate the virtual environment
                deactivate
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
