#Testes de integração com o Cucumber

* Isto irá virar o índice (este texto será removido).
{:toc}

O [Cucumber][] é a melhor opção para realizar os testes de integração das suas
aplicações Merb.
Cucumber é uma ferramenta que pode executar "documentação de funcionalidades"
escritas em texto comum.
Aqui está um exemplo de uma especificação funcional (feature) típica no
Cucumber:

    Feature: Login
      To ensure the safety of the application
      A regular user of the system
      Must authenticate before using the app

      Scenario: Failed Login
        Given I am not authenticated
        When I go to /login
        And I fill in "login" with "i_dont_exist"
        And I fill in "password" with "and_i_dont_have_a_password"
        And I press "Log In"
        Then the login request should fail
        Then I should see an error message

## Merb e Cucumber

Para usar o Cucumber com o Merb, você precisa instalar o plugin
[merb\_cucumber][].
Para instalar o plugin, execute o comando

    $ sudo gem install merb_cucumber

ou, se você está usando o diretório de gems local, execute

    $ thor merb:gem:install merb_cucumber

Depois, na raiz do seu projeto merb, execute

    $ merb-gen cucumber

Ou, para instalar com suporte ao [Webrat][], execute

    $ merb-gen cucumber --session-type webrat

Isto também irá instalar a feature login mostrada acima.
Este teste deverá passar se você estiver usando merb-auth.

Executando suas features é muito simples. Basta executar

    $ rake features

## Criando novas features

Para adicionar a definição de uma nova feature na sua aplicação Merb, execute

    $ merb-gen feature FEATURE_NAME

Uma nova feature chamada FEATURE\_NAME.feature será criada no diretório
features. Ela se parecerá com isto:

    Feature: add comment
      To [accomplish some goal]
      A [role]
      Does [something]

      Scenario: [first scenario]
        Given [precondition]
            And [another precondition]
        When [event happens]
        And [another event happens]
        Then [outcome]
        And [another outcome]

        Scenario: [other scenario]
          Given [precondition]
            And [another precondition]
          When [event happens]
          And [another event happens]
          Then [outcome]
          And [another outcome]

Se você executar suas features a partir da linha de comando, você verá que o
Cucumber irá mostrar dicas sobre como implementar cada passo. Mais informações
sobre a implementação de features no Cucumber podem ser encontradas no
[Cucumber wiki].

<!-- Links -->
[Cucumber]:         http://github.com/aslakhellesoy/cucumber/wikis/home
[Cucumber wiki]:    http://github.com/aslakhellesoy/cucumber/wikis/home
[merb\_cucumber]:   http://github.com/david/merb_cucumber/tree/master
[Webrat]:           http://github.com/brynary/webrat/wikis
