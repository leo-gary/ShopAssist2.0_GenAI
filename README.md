# ShopAssist2.0_GenAI

1. Background on Shop Assistant AI
Shop Assistant AI leverages OpenAI's advanced language models to enhance the online shopping experience. By integrating AI capabilities, it provides personalized product recommendations, answers customer queries, and assists with order processing. 
This tool aims to streamline customer interactions, reduce cart abandonment, and boost sales through intelligent automation. In ShopAssist 2.0 major focus was 
o	to improve the overall system design to improve the LLM output to give more consistent output by improving the user requirement structure using schema for required input.
2. Problem Statement
In the competitive e-commerce landscape, customers often face challenges such as overwhelming product choices, lack of personalized assistance, and difficulty in finding specific items. These issues can lead to frustration and increased cart abandonment rates. 
The goal of Shop Assistant AI 2.0 is to address these pain points by providing a seamless, interactive, and personalized shopping experience and make sure consistent output using function calling APIs.
Major problem with the Shop Assistant AI 1.0 
o	Sometimes the user requirement input conversion to JSON is not consistent
o	Conversion of data from input database to JSON format is not consistent


3. Example Datasheet
 





4. Overall chatbot design 

 
5. Approach Using Function Calling
Function calling in OpenAI's API allows the Shop Assistant AI to interact with external tools and APIs. This involves defining functions that the AI can call to perform specific tasks, such as fetching product details or processing orders. The typical sequence includes:
1.	Defining Functions: Describe the functions in the API call.
2.	Calling Functions: The AI generates a JSON object with arguments for the functions.
3.	Executing Functions: Parse the JSON and call the functions in your code.
4.	Returning Results: Append the function response to the AI's conversation

6. System Functionality
User Interaction Flow:
1.	User Input: The user interacts with the AI through a chat interface, asking for product information or assistance.
2.	Intent Detection: The AI detects the user's intent (e.g., asking for laptop details).
3.	Function Call for Product Map Layer: The AI uses a function call to retrieve product details from the product map layer.
4.	Chat Completion with Function Call: The AI generates a chat response using the retrieved product details.
5.	Laptop Description Conversion: The AI converts the laptop description string to JSON format using a function call.
6.	Intent Confirmation: The AI confirms the user's intent and extracts user input in JSON format.
7. System Components:
1.	Function Call Handler: Manages function calls to retrieve and process product information.
2.	Product Map Layer: Contains detailed product information, including laptop descriptions.
3.	JSON Converter: Converts product descriptions to JSON format.
4.	Intent Confirmation Module: Confirms user intent and extracts input in JSON format.
5.	Response Generator: Generates chat responses based on processed data.
8. Major Functions
•	Initialize_conversation(): Initialize conversation with system message, prompt message , chain of thoughts to keep the conversation till all necessary data is collected, few shot prompting with sample conversation
•	moderation_check(): To check if the user input and bot response is inappropriate. If inappropriate then break the conversation and end it.
•	Intent_confirmation_layer(): It takes the assistant response and evaluates if the chatbot has capture all the required field or not like GPU, Multitasking, Processing speed, Display quality, Portability, Budget in low/High/Medium except budget , budget is in numerical values. Return Yes, incase all values correctly received, incase not return No with reason.
•	get_chat_completion_func_calling() : Firstly : This is major function to call the get chat completion along with function calling schema, this helps to get the exact required field as requested from the user requirement in JSON format with must required fields, secondly :  it helps to convert the laptop description in the csv file or database to JSON format for comparison with user requirement.
•	initialize_conv_reco() : Starts a recommendation conversation, it list the recommendation in string format to the user. Takes the product information and give the recommendation to user.
