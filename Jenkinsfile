pipeline{
    agent any
        stages {
            stage('Opcao Ambiente'){
                steps {
                    script {
                    env.AMBIENTE_BUILD = input message: 'Escolha o ambiente de build:', ok: 'Release!',
                    parameters: [choice(name: 'AMBIENTE_BUILD', choices: 'Desenvolvimento\nProducao', description: 'Qual é o ambiente a ser escolhido?')]
                }
                echo "${env.AMBIENTE_BUILD}"
            }
        }
        stage ('Deploy em Desenvolvimento'){
            when {
                expression { "${env.AMBIENTE_BUILD}" == 'Desenvolvimento' }
        }
            steps {
                echo 'O Deploy será realizado em DESENV'
            }
        }
        stage ('Deploy em Produção'){
            when {
                expression { "${env.AMBIENTE_BUILD}" == 'Producao' }
        }
            steps {
                echo 'O Deploy será realizado em PROD'
            }
        }
    }
}
