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

                # Assuming Miniconda is installed and the conda command is available
                # Check if the mlip environment exists
                if ! conda info --envs | grep mlip; then
                    echo 'Creating a new Conda environment named mlip.'
                    conda create -n mlip python=3.8 pytest numpy pandas scikit-learn -c conda-forge -y
                else
                    echo 'Conda environment mlip already exists.'
                fi
                
                # Activate the Conda environment
                source activate mlip

                # The required packages are already installed during the environment creation
                # If you need to install any additional packages, you can do so with conda install or pip install commands here

                # Run pytest
                pytest

                # Note: No need to explicitly deactivate in a script, as each step runs in a new shell
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
