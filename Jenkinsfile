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

                # Activate the Python virtual environment
                # Ensure to replace <path_to_mlip> with the actual path to your mlip virtual environment directory
                python3 -m venv mlip
                source mlip/bin/activate

                pip install pytest

                pip install numpy

                pip install pandas

                pip install requests

                pip install scikit-learn

                # Run pytest
                pytest test_utility.py

                # Deactivate the virtual environment
                deactivate

                # Note: Jenkins will mark the build as failed if any command returns a non-zero exit code
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
