pipeline {
    agent any                 // Runs on any available agent/node
    environment {
        APP_ENV = 'production'
        VERSION = '1.0.0'}
    stages {
        stage('Checkout') {
            steps {
                checkout scm    // Pulls code from repo
            }}
        stage('Build') {
            steps {
                echo "Building the application..."
                sh 'echo build command here'}    }
        stage('Test') {
            steps {
                echo "Running tests..."
                sh 'echo test command here'}}
        stage('Deploy') {
            steps {
                echo "Deploying to production..."
                sh 'echo deploy command here'}}}

    post {
        success {
            echo 'Pipeline succeeded!' }
        failure {
            echo 'Pipeline failed!'
        } }}
FlUTTER pipeline {
  agent any

  environment {
    FLUTTER_HOME = "D:\\flutter_dev\\flutter"
    PATH = "${FLUTTER_HOME}\\bin;${env.PATH}"
  }

  stages {
    stage('Checkout') {
      steps {
        echo "Cloning repository..."
        checkout scm
      }
    }

    stage('Flutter Doctor') {
      steps {
        echo "Checking Flutter setup..."
        bat 'flutter doctor -v'
      }
    }

    stage('Pub Get') {
      steps {
        echo "Fetching dependencies..."
        bat 'flutter pub get'
      }
    }

    stage('Analyze') {
      steps {
        echo "Analyzing code..."
        bat 'flutter analyze'
      }
    }

    // stage('Run Tests') {
    //   steps { bat 'flutter test --coverage' }
    // }

   // stage('Build APK') {
    //  steps {
     //   echo "Building Flutter APK (debug)..."
     //   bat 'flutter build apk --debug'
     // }
   // }

    stage('Archive') {
      steps {
        echo "Archiving artifacts..."
        archiveArtifacts artifacts: '**/build/app/outputs/flutter-apk/app-debug.apk', allowEmptyArchive: true
      }
    }
  }

  post {
    success {
      echo '✅ Build completed successfully!'
    }
    failure {
      echo '❌ Build failed. Check logs for details.'
    }
  }
}

