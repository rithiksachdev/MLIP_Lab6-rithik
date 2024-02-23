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
                # Initialize Conda
                sudo /home/team03/miniconda3/condabin/conda init

                # Create a new Conda environment named myenv
                sudo /home/team03/miniconda3/condabin/conda create -n myenv python=3.8 pytest numpy pandas scikit-learn -c conda-forge -y

                # Activate the Conda environment
                sudo /home/team03/miniconda3/condabin/conda activate myenv

                # Run pytest within the environment
                pytest

                # Note: 'sudo' is generally not recommended for activating environments or running user-space tools like pytest. It should only be used if absolutely necessary for permissions reasons, and with great care.


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
