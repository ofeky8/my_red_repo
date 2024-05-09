
pipeline {
    agent

    stages {

        stage('Parameters') {
            steps {
                script {
                    properties([
                        parameters([
                            choice(name:"engineName",choices:['Cobalt','Azure'],description: "Choose Engine"),
                            [$class: 'CascadeChoiceParameter',
                                choiceType: 'PT_CHECKBOX',
                                description: 'Select entities',
                                filterLength: 1,
                                filterable: true,
                                name: 'entities',
                                randomName: 'choice-parameter-5631314439613978',
                                script: [
                                    $class: 'GroovyScript',
                                    fallbackScript: [
                                        classpath: [],
                                        sandbox: false,
                                        script:
                                            'return[\'Could not get entities\']'
                                    ],
                                    script: [
                                        classpath: [],
                                        sandbox: false,
                                        script:
                                            '''
                                               if(engineName.equals('Cobalt')){
                                               return["1","2","3"]
                                               } else {
                                               return["4","5","6"]}
                                            '''
                                    ]
                                ]

                            ]

                        ])
                    ])
                }
            }
        }


    }

}

