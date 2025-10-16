# 🌐 Web MQTT Client Dashboard (Dark Mode)

A modern, responsive, and feature-rich MQTT client interface built with **Tailwind CSS** and the **Paho MQTT JavaScript client**. It mimics the **Gemini Dark Mode** aesthetic and includes client-side automation logic.

---

## 🚀 Features

* **Gemini Dark Mode UI:** Deep, high-contrast dark theme (Slate/Teal/Indigo) optimized for extended use.
* **Fully Responsive:** Excellent user experience on both desktop and mobile devices.
* **Local Automations (Edge Triggering):** Define rules that automatically trigger a publication when the payload of a subscribed topic changes and meets a specified JavaScript condition (e.g., `T:/sensor/temp > 25`).
* **Persistent Configuration:** Connection settings and automations are saved locally using `localStorage`.
* **Core MQTT Functionality:** Connect/Disconnect, Subscribe/Unsubscribe (with QoS selection), and Quick Publish (with QoS and Retain options).

---

## 🛠️ Project Structure

The project consists of two main files:

1.  **`index.html` (Connection/Login):** Handles broker configuration and client connection.
2.  **`dashboard.html` (Main Interface):** Provides the subscription, publishing, and automation features.

### 1. index.html (Login)

Allows the user to input the MQTT Broker address, port, credentials (Username/Password), and connection options (Client ID generation, Keep Alive, Clean Session).

### 2. dashboard.html (Dashboard)

The main operational hub, divided into two sections:

* **Sidebar (md:w-1/3):** Manages **Active Subscriptions** and lists **Saved Automations**.
* **Main Area (md:w-2/3):** Contains forms for **Creating Automations**, **Quick Publishing**, and the **Message Feed**.

---

## 🧠 Automation Logic Guide

The dashboard supports powerful local automation rules using standard JavaScript expressions.

### **Syntax**

Use the prefix **`T:/your/topic/path`** within the `Logic` field to reference the last received payload of that topic.

| Variable | Description |
| :--- | :--- |
| **`T:/topic/path`** | Replaced by the last **payload** received on this topic. |
| **`==`**, **`>`**, **`<`**, **`&&`**, **`||`** | Standard JavaScript comparison and logical operators. |

### **Examples**

| Condition | Description |
| :--- | :--- |
| `T:/sensor/temp > 30` | Trigger if the temperature is **greater than 30**. |
| `T:/switch/status == "ON"` | Trigger if the status message is exactly `"ON"`. |
| `(T:/sensor/lux < 10) && (T:/time/hour > 18)` | Trigger if it's **dark** AND the time is **after 6 PM**. |

***Note:*** *The system uses an **edge trigger**—the action only publishes when the logic state changes from `FALSE` to `TRUE` to prevent continuous publishing.*

---
---

# 🇧🇷 Cliente Web MQTT Dashboard (Modo Escuro)

Uma interface de cliente MQTT moderna, responsiva e rica em recursos, construída com **Tailwind CSS** e o **cliente JavaScript Paho MQTT**. Ela mimetiza a estética do **Modo Escuro do Gemini** e inclui lógica de automação do lado do cliente.

---

## 🚀 Recursos

* **Interface no Modo Escuro Gemini:** Tema escuro profundo e de alto contraste (Slate/Teal/Indigo) otimizado para uso prolongado.
* **Totalmente Responsivo:** Excelente experiência de usuário em dispositivos desktop e móveis.
* **Automações Locais (Disparo de Borda):** Defina regras que disparam automaticamente uma publicação quando o payload de um tópico subscrito muda e atende a uma condição JavaScript específica (ex: `T:/sensor/temp > 25`).
* **Configuração Persistente:** As configurações de conexão e automações são salvas localmente usando `localStorage`.
* **Funcionalidade MQTT Essencial:** Conectar/Desconectar, Subscrever/Desubcrever (com seleção de QoS) e Publicação Rápida (com opções de QoS e Retain).

---

## 🛠️ Estrutura do Projeto

O projeto consiste em dois arquivos principais:

1.  **`index.html` (Conexão/Login):** Gerencia a configuração do broker e a conexão do cliente.
2.  **`dashboard.html` (Interface Principal):** Fornece os recursos de subscrição, publicação e automação.

### 1. index.html (Login)

Permite ao usuário inserir o endereço do Broker MQTT, porta, credenciais (Nome de Usuário/Senha) e opções de conexão (Geração de Client ID, Keep Alive, Clean Session).

### 2. dashboard.html (Dashboard)

O hub operacional principal, dividido em duas seções:

* **Barra Lateral (md:w-1/3):** Gerencia **Subscrições Ativas** e lista **Automações Salvas**.
* **Área Principal (md:w-2/3):** Contém formulários para **Criação de Automações**, **Publicação Rápida** e o **Feed de Mensagens**.

---

## 🧠 Guia de Lógica de Automação

O dashboard suporta poderosas regras de automação locais usando expressões JavaScript padrão.

### **Sintaxe**

Use o prefixo **`T:/caminho/do/seu/topico`** dentro do campo `Lógica` para referenciar o último payload recebido desse tópico.

| Variável | Descrição |
| :--- | :--- |
| **`T:/caminho/do/topico`** | Substituído pelo último **payload** recebido neste tópico. |
| **`==`**, **`>`**, **`<`**, **`&&`**, **`||`** | Operadores lógicos e de comparação padrão do JavaScript. |

### **Exemplos**

| Condição | Descrição |
| :--- | :--- |
| `T:/sensor/temp > 30` | Dispara se a temperatura for **maior que 30**. |
| `T:/switch/status == "ON"` | Dispara se a mensagem de status for exatamente `"ON"`. |
| `(T:/sensor/lux < 10) && (T:/time/hour > 18)` | Dispara se estiver **escuro** E o horário for **depois das 18h**. |

***Nota:*** *O sistema usa um **disparo de borda** (edge trigger)—a ação só publica quando o estado da lógica muda de `FALSO` para `VERDADEIRO` para evitar publicações contínuas.*
