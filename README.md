# Jenkins Pipes HelloWorld

A minimal and stupid "helloworld" example project for the [Jenkins Pipes](https://github.com/abhishekbhonde/Hello-World-SpringBoot-.git) demo:

 * the `Jenkinsfile` describes **HOW** to build this project in [Pipeline-DSL](https://github.com/abhishekbhonde/Hello-World-SpringBoot-.git)


## How it works

The `Jenkinsfile` in here describes **HOW** this project is built, in terms of the individual stages that make up the build pipeline and what happens within them:

```groovy
pipeline {
    agent any 
    tools {
        maven "Maven3"
    }
    stages {
        stage('Compile') { 
            steps {
                git 'https://github.com/abhishekbhonde/Hello-World-SpringBoot-.git'
                sh 'mvn compile'
            }
        }
        stage('Test') { 
            steps {
                git 'https://github.com/abhishekbhonde/Hello-World-SpringBoot-.git'
                sh 'mvn test'
            }
        }
        stage('Package') { 
            steps {
                git 'https://github.com/abhishekbhonde/Hello-World-SpringBoot-.git'
                sh 'mvn package'
            }
        }
        stage('Deploy') { 
            steps {
                sh 'echo "Deployement Successfull"'
            }
        }
    }
}
```

The `master` branch build should succeed:

![image](https://cloud.githubusercontent.com/assets/365744/22727812/3ad04a26-eddb-11e6-9dd9-5d2e5a975f22.png)

The `feature/make-it-fail` branch shows how a build failure looks like:

![image](https://cloud.githubusercontent.com/assets/365744/22727851/688829b6-eddb-11e6-8233-6503c5a6fa49.png)


