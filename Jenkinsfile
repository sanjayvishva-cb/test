pipeline {
    agent {
        kubernetes {
            yaml '''
                apiVersion: v1
                kind: Pod
                spec:
                  containers:
                  - name: jnlp
                    image: jenkins/inbound-agent:latest
            '''
        }
    }
    stages {
        stage('Build') {
            steps {
                echo "=== Team Build Stage Running ==="
                sh 'echo "Simulating build output" > build-output.txt'
                sh 'ls -la'
            }
        }
        stage('Test') {
            steps {
                echo "=== Team Test Stage Running ==="
                sh 'echo "All tests passed" >> build-output.txt'
            }
        }
    }
    post {
        always {
            echo "=== Team post{} block — no SBOM here ==="
        }
    }
}
