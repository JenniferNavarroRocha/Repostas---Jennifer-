# Repostas---Jennifer-
*** Settings ***
Library    SeleniumLibrary

*** Variables ***
${URL}    https://www.saucedemo.com/
${USERNAME}    standard_user
${PASSWORD}    secret_sauce

*** Test Cases ***
Adicionar Itens ao Carrinho e Finalizar Compra
    Abrir Navegador    ${URL}
    Preencher Campo    id:user-name    ${USERNAME}
    Preencher Campo    id:password    ${PASSWORD}
    Clicar Botão    id:login-button
    Clicar Botão    xpath://button[text()='ADD TO CART']
    Clicar Botão    xpath://a[@class='shopping_cart_link']
    Clicar Botão    xpath://a[text()='CHECKOUT']
    Aguardar Elemento    xpath://h2[text()='Checkout: Overview']
    Should Contain    Thank you for your order!
    Fechar Navegador
