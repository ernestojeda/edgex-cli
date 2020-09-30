//
// Copyright (c) 2020 Intel Corporation
//
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at
//
//      http://www.apache.org/licenses/LICENSE-2.0
//
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.
//

pipeline {
    agent { label 'ubuntu18.04-docker-8c-8g' }
    environment {
        ARCH = 'x86_64'
    }
    stages {
        stage('Test') {
            agent {
                dockerfile {
                    filename 'Dockerfile.build'
                    additionalBuildArgs '--build-arg BASE=nexus3.edgexfoundry.org:10003/edgex-devops/edgex-golang-base:1.15-alpine'
                    reuseNode true
                }
            }
            steps {
                sh 'make test'
            }
        }
    }
}