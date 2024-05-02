pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Create a directory for out-of-source build
                dir('build') {
                    // Run CMake to configure the build
                    sh 'cmake -G Ninja -DCMAKE_BUILD_TYPE=Debug -DLLVM_ENABLE_PROJECTS=clang ../llvm'
                    
                    // Build the project
                    sh 'ninja -j 8 check-clang'
                }
            }
        }
    }
    post {
        always {
            // Clean up
            deleteDir()
        }
    }
}