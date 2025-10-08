pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                // Pull code from GitHub
                git branch: 'main', url: 'https://github.com/Pavankalyan29/Atm'
            }
        }

        stage('Install Dependencies (Optional)') {
            steps {
                echo 'No dependencies required for plain HTML/CSS/JS.'
                // If you had Node packages:
                // sh 'npm install'
            }
        }

        // stage('Run Simple Test (Optional)') {
        //     steps {
        //         echo 'No automated tests yet, but you could run JS lint or browser tests.'
        //         // Example: run ESLint
        //         // sh 'npx eslint app.js'
        //     }
        // }

        stage('Lint Code') {
            steps {
                echo 'Checking HTML, CSS, and JS syntax...'
                sh 'htmlhint index.html'
                sh 'stylelint "**/*.css"'
                sh 'eslint app.js'
            }
        }


        stage('Archive Project') {
            steps {
                // Save files as artifacts in Jenkins
                archiveArtifacts artifacts: '**/*.html, **/*.css, **/*.js', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Pipeline finished successfully!'
        }
        failure {
            echo 'Pipeline failed. Check console logs.'
        }
    }
}
