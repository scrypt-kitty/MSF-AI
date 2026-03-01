# MSF-AI : AI Assistant for Metasploit Framework

This project is an artificial intelligence assistant designed to interact with the Metasploit Framework. It provides a conversational natural language interface for executing various penetration testing tasks, from reconnaissance to exploitation and reporting.

## 🚀 Features

*   **Conversational AI**: Interact with Metasploit using simple, natural phrases.
*   **Task Orchestration**: Break down complex objectives (e.g., "scan and exploit") into a series of automatically executed steps.
*   **Modular Architecture (MVC)**: The project is structured following the MVC (Model-View-Controller) design pattern, making it easy to maintain and extend.
*   **Tool Integration**: The assistant can use a variety of tools for reconnaissance, post-exploitation, web application testing, and report generation.
*   **RAG (Retrieval-Augmented Generation)**: The AI can query a knowledge base to provide more accurate and contextual responses.

## 🏗️ Architecture

The project consists of the following components:

*   **Controller (`msf_controller.py`)**: This is the main entry point of the application. It handles user input, coordinates actions between the AI and Metasploit, and bridges the model and view.
*   **Model (`msf_model.py`)**: Represents the business logic. It manages the connection to the Metasploit RPC server and executes commands.
*   **View (`msf_view.py`)**: Handles the command-line user interface, including displaying banners, statuses, and AI responses.
*   **Orchestrator (`msf_orchestrator.py`)**: Enables breaking down high-level objectives into smaller tasks and executing them sequentially.
*   **RAG (`msf_rag.py`)**: Builds and uses a vector knowledge base to improve the relevance of AI responses.

## 📋 Prerequisites

Before getting started, make sure you have the following installed:

*   **Python 3.8+**
*   **Metasploit Framework**
*   A **DeepSeek AI** account to obtain an API key.

## ⚙️ Installation

1.  **Clone the Git repository:**
    ```bash
    git clone https://github.com/iamarketings/MSF-AI.git
    cd MSF-AI
    ```

2.  **Install Python dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Configure environment variables:**
    Create a `.env` file in the project root (`msf_aiv4/.env`) and add the following:

    ```
    DEEPSEEK_API_KEY="YOUR_DEEPSEEK_API_KEY"
    MSF_RPC_USER="msf"
    MSF_RPC_PASS="YOUR_MSF_PASSWORD"
    MSF_RPC_PORT="55553"
    ```

4.  **Start the Metasploit RPC server:**
    Open a terminal and launch `msfconsole`. Then use the following command to start the RPC server with a username and password:
    ```bash
    msfconsole -x "load msgrpc Pass=YOUR_MSF_PASSWORD User=msf"
    ```
    Make sure the password matches what you configured in the `.env` file.

## ▶️ Usage

Once the Metasploit RPC server is running, you can launch the AI assistant:

```bash
python msf_aiv4/msf_controller.py
```

The assistant will display a welcome banner and you can start interacting with it by entering natural language commands.

**Example commands:**

*   `search for exploits for eternalblue`
*   `scan ports on 192.168.1.10`
*   `exploit the vsftpd service on 10.0.0.5` (orchestration mode)

## 🛠️ Available Tools

The assistant has a set of tools to perform different actions:

*   **Reconnaissance**: Search for modules, IP geolocation, etc.
*   **Network**: Port scanning, etc.
*   **Web**: Web vulnerability scanning, etc.
*   **Post-Exploitation**: Execute commands on a session, etc.
*   **Reporting**: Generate reports.

## Versions

*   **v3**: Previous version of the assistant.
*   **v4**: Current version, with improved architecture, task orchestration, and RAG integration.
