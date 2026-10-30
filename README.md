# Jetnews App (Accessibility in Jetpack Compose)

Este repositório contém a implementação do codelab prático da Google sobre **Acessibilidade (a11y) no Jetpack Compose**, utilizando como base o aplicativo de notícias **Jetnews**.

O objetivo do projeto é transformar uma aplicação funcional em uma experiência totalmente inclusiva, garantindo que utilizadores de leitores de ecrã (como o TalkBack), pessoas com baixa visão ou limitações motoras consigam navegar e interagir de forma natural e eficiente.

## Tecnologias e Recursos de Acessibilidade

- **Linguagem:** Kotlin
- **UI Framework:** Jetpack Compose (Material Design 3)
- **Acessibilidade (a11y):**
  - Configuração e customização de `semantics`
  - Fusão de nós semânticos com `clearAndSetSemantics` e `mergeDescendants = true`
  - Definição correta de `contentDescription` em elementos decorativos e informativos
  - Aumento do tamanho mínimo de alvo de toque (*Touch Target Size* - mínimo de 48dp x 48dp)
  - Aumento e ajuste de taxa de contraste de cores (WCAG compliance)
  - Ações personalizadas no leitor de ecrã (`customActions`)
- **IDE:** Android Studio
- **Ferramentas de Auditoria:** Accessibility Scanner / TalkBack no emulador Android

## Conceitos e Aprendizados Práticos

Durante o desenvolvimento e otimização da acessibilidade do Jetnews, foram aplicadas as seguintes técnicas:

### 1. Ajuste de Alvos de Toque (*Touch Targets*)
- Garantia de que botões, ícones clicáveis e elementos de seleção possuem dimensões mínimas de **48dp x 48dp** utilizando `Modifier.defaultMinSize(minWidth = 48.dp, minHeight = 48.dp)` ou `IconButton` apropriados, facilitando a interação de pessoas com limitações motoras.

### 2. Melhoria no Suporte ao TalkBack (*Semantics & Content Descriptions*)
- Eliminação de leitura redundante de texto em elementos de imagem decorativos através do envio de `contentDescription = null`.
- Atribuição de descrições claras e contextuais em ícones interativos (ex.: botões de favorito, partilha e navegação no `AppDrawer` e no `ArticleScreen`).

### 3. Agrupamento e Fusão de Nós Semânticos (*Semantic Node Merging*)
- Uso do modificador `Modifier.semantics(mergeDescendants = true)` para agrupar múltiplos elementos de texto e imagens de um cartão de notícia (`PostCardHistory`) em um único bloco focalizável no TalkBack. Isso evita que o leitor de ecrã leia o título, a data e a foto como elementos isolados.

### 4. Ações Personalizadas do Leitor de Ecrã (*Custom Actions*)
- Implementação de `customActions` em cartões de lista para permitir que ações secundárias (como "Marcar como não favorito") sejam acessadas diretamente pelo menu de ações do TalkBack sem sobrecarregar a navegação do utilizador.

### 5. Ajustes de Contraste e Temas
- Correção das cores de texto e superfícies no arquivo `Color.kt` e `Theme.kt` para garantir que o contraste atinja as métricas exigidas pelas diretrizes WCAG AA/AAA.

## Como Executar o Projeto

1. Clone o repositório:
   ```bash
   git clone https://github.com/leticia-farias/compose-training-accessibility-jetnews.git
2. Abra o projeto no Android Studio.
3. Aguarde a sincronização do Gradle.
4. Conecte um dispositivo físico ou emulador (API 21+).
5. Ative o TalkBack nas configurações do dispositivo (Configurações > Acessibilidade > TalkBack) para testar os focos semânticos e leituras de voz.
