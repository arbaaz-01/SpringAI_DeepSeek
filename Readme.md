DeepSeek Chat - Local DeepSeek AI Chat Application

A Spring Boot application that enables you to run the DeepSeek AI model locally using Spring AI. This project provides a React-based frontend for interacting with the DeepSeek model and exposes RESTful APIs for direct usage. The model runs entirely on your local machine, offering privacy and control, with performance heavily dependent on your system's configuration.

Project Overview

Model: Utilizes the DeepSeek 1.5 billion parameter model, an entry-level and basic model suitable for lightweight tasks. Users with more powerful systems can experiment with higher-parameter models (e.g., 7B or 13B) depending on hardware capabilities.


Local Execution: The model runs locally, ensuring data privacy and eliminating dependency on external APIs. Performance (e.g., response time, handling complex queries) depends on your CPU, GPU, RAM, and storage configuration.



Frontend: A modern React-based UI for a seamless chat experience.



Backend: Spring Boot with Spring AI integration for managing the DeepSeek model.

Check out the working video to see the application in action!



Watch the Demo Video


This video demonstrates the setup process, frontend usage, and sample interactions with the DeepSeek model.

Prerequisites





Java 17+: Ensure you have JDK 17 or higher installed.



Maven: For building the Spring Boot application.



Node.js and npm: For the React frontend (included in the static resources).



Ollama: A lightweight framework to run the DeepSeek model locally.



System Requirements: Minimum 8GB RAM, 4-core CPU, and 10GB free storage. Higher specs recommended for larger models.

Setup Instructions

1. Install Ollama





Download and install Ollama from its official site.



Follow the installation instructions for your operating system (Linux, macOS, or Windows).

2. Pull the DeepSeek Model





Open a terminal and run the following command to pull the DeepSeek 1.5B parameter model:

ollama pull deepseek-coder:1.5b



For users with capable hardware, you can pull larger models (e.g., deepseek-coder:7b or deepseek-coder:13b) by replacing the model name.

3. Start Ollama Serve





Run the Ollama server to make the model available:

ollama serve



Ensure the server is running on the default port (typically 11434). You can verify by accessing http://localhost:11434 in your browser.

4. Clone the Repository





Clone this repository to your local machine:

git clone https://github.com/your-username/codecraft.git
cd codecraft

5. Configure Application Properties





Open src/main/resources/application.properties and add the following configuration:

spring.ai.ollama.chat.enabled=true
spring.ai.ollama.chat.base-url=http://localhost:11434
spring.ai.ollama.chat.model=deepseek-coder:1.5b



Adjust the base-url if Ollama is running on a different port or machine.



Update the model value if you pulled a different DeepSeek variant.

6. Build and Run the Application





Build the project using Maven:

mvn clean install



Run the Spring Boot application:

mvn spring-boot:run



The application will be available at http://localhost:8080.

7. Access the Frontend





Open your browser and navigate to http://localhost:8080.



Start interacting with the DeepSeek model via the chat interface.

Endpoints

If you prefer to use the API directly without the frontend:





/ai/generate: Returns a single response for a given prompt.





Method: GET



Parameter: message (e.g., ?message=Write a Java program)



Example: http://localhost:8080/ai/generate?message=Hello



Response: JSON with a "generation" field containing the model's output.



/ai/generateStream: Streams the response for a given prompt.





Method: GET



Parameter: message (e.g., ?message=Write a Java program)



Example: http://localhost:8080/ai/generateStream?message=Hello



Response: Streaming ChatResponse objects.

Use tools like curl or Postman to test these endpoints:

curl "http://localhost:8080/ai/generate?message=Tell me a joke"

Important Notes





Local Performance: Since the model runs locally, the response speed and capability depend on your system's hardware. A system with a GPU and sufficient RAM (e.g., 16GB+) will handle larger models and complex queries better.



Model Scalability: The default 1.5B parameter model is lightweight but limited. Upgrading to 7B or 13B models requires more resources but offers improved accuracy and context handling.



Troubleshooting: If the model fails to load, ensure Ollama is running and the application.properties settings match your setup. Check logs in the terminal for errors.

Contributing

Contributions are welcome! Please fork the repository and submit pull requests for any enhancements or bug fixes. Ensure to follow the existing code style and include tests where applicable.


Acknowledgments





Built with Spring Boot and Spring AI.



Powered by the Ollama framework and the DeepSeek model.



Frontend developed with React and Tailwind CSS.