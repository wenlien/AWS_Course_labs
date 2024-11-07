# Labs memos of "Developing Generative AI Applications on AWS" by using Playground

#### Task 1: Perform Text Generation

###### Task 1-1: Perform Text Generation
    Steps: Amazon Bedrock -> Playgrounds -> Chat/text
<img width="699" alt="Screenshot 2024-11-07 at 5 30 50 PM" src="https://github.com/user-attachments/assets/560c000c-ded7-4fd5-8a13-3288fee35dae">

    Mode: ***Single prompt***

    Model: ***amazon.titan-text-express-v1***

    Parameters:

```json
{
    "maxTokenCount":8192(4096),
    "stopSequences":[],
    "temperature":0,
    "topP":0.9
}
```

    Prompt:

```textile
Command: Write an email from Bob, Customer Service Manager, AnyCompany to the customer "John Doe" 
who provided negative feedback on the service provided by our customer support 
engineer
```

    Example Output:

```textile
```

###### Task 1-2: Perform Text Generation using a prompt that includes Context

    Mode: ***Single prompt***

    Model: ***meta.llama3-8b-instruct-v1:0***

    Parameters:

```json
{
    "max_gen_len": 512,
    "temperature": 0,
    "top_p": 1
}
```

    Prompt:

```textile
Human: Create an apology email from the Service Manager {customerServiceManager} at AnyCompany to {customerName} in response to the following feedback that was received from the customer: 
<customer_feedback>
{feedbackFromCustomer}
</customer_feedback>
Assistant:
```

    Input:

```json
{
    "customerServiceManager": "Bob Smith", 
    "customerName": "John Doe", 
    "feedbackFromCustomer": "Hello Bob,
I am very disappointed with the recent experience I had when I called your customer support.
I was expecting an immediate call back but it took three days for us to get a call back.
The first suggestion to fix the problem was incorrect. Ultimately the problem was fixed after three days.
We are very unhappy with the response provided and may consider taking our business elsewhere."
}
```

    Example Output:

```textile
```

#### Task 2: Create Text Summarization

#### Task 2-1: Text summarization with small files with Titan Text Premier

    Mode: ***Single prompt***

    Model: ***amazon.titan-text-premier-v1:0***

    Parameters:

```json
{
    "maxTokenCount":2048,
    "stopSequences":[],
    "temperature":0,
    "topP":0.9
}
```

    Prompt:

```text
Please provide a summary of the following text:

AWS took all of that feedback from customers, and today we are excited to announce Amazon Bedrock, \
a new service that makes FMs from AI21 Labs, Anthropic, Stability AI, and Amazon accessible via an API. \
Bedrock is the easiest way for customers to build and scale generative AI-based applications using FMs, \
democratizing access for all builders. Bedrock will offer the ability to access a range of powerful FMs \
for text and images—including Amazons Titan FMs, which consist of two new LLMs we’re also announcing \
today—through a scalable, reliable, and secure AWS managed service. With Bedrock’s serverless experience, \
customers can easily find the right model for what they’re trying to get done, get started quickly, privately \
customize FMs with their own data, and easily integrate and deploy them into their applications using the AWS \
tools and capabilities they are familiar with, without having to manage any infrastructure (including integrations \
with Amazon SageMaker ML features like Experiments to test different models and Pipelines to manage their FMs at scale).
```

    Example Output:

```textile
```

#### Task 2-2: Abstractive Text Summarization

    Mode: ***Chat***

    Model: ***meta.llama3-8b-instruct-v1:0***

    Parameters:

```json
{
    "max_gen_len": 2048,
    "temperature": 0,
    "top_p": 1
}
```

    Prompt:

```textile
summarize the file 2022-letter.txt
```

    Input: 2022-letter.txt

    Example Output:

```textile
```

#### Task 3: Use Amazon Bedrock for Question Answering

###### Task 3-1:

    Mode: ***Single prompt***

    Model: ***amazon.titan-text-express-v1***

    Parameters:

```json
{
    "maxTokenCount":512,
    "stopSequences":[],
    "temperature":0,
    "topP":0.9
}
```

    Prompt:

```textile
You are an helpful assistant. Answer questions in a concise way. If you are unsure about the
answer say 'I am unsure'

Question: How can I fix a flat tire on my AnyCompany AC8?
Answer:
```

    Input:

    Example Output:

```textile
```

###### Task 3-2:

    Mode: ***Single prompt***

    Model: ***amazon.titan-text-express-v1***

    Parameters:

```json
{
    "maxTokenCount":512,
    "stopSequences":[],
    "temperature":0,
    "topP":0.9
}
```

    Prompt:

```textile
How can I fix a flat tire on my Amazon Tirana?
```

    Input:

    Example Output:

```textile
```

###### Task 3-3:

    Mode: ***Single prompt***

    Model: ***amazon.titan-text-express-v1***

    Parameters:

```json
{
    "maxTokenCount":512,
    "stopSequences":[],
    "temperature":0,
    "topP":0.9
}
```

    Prompt:

```textile
Answer the question based only on the information provided between ## and give step by step guide.
#
{context}
#

Question: {question}
Answer:
```

    Input:

```json
{
    "question": "How can I fix a flat tire on my AnyCompany AC8?",
    "context": "Tires and tire pressure:

Tires are made of black rubber and are mounted on the wheels of your vehicle. They provide the necessary grip for driving, cornering, and braking. Two important factors to consider are tire pressure and tire wear, as they can affect the performance and handling of your car.

Where to find recommended tire pressure:

You can find the recommended tire pressure specifications on the inflation label located on the driver's side B-pillar of your vehicle. Alternatively, you can refer to your vehicle's manual for this information. The recommended tire pressure may vary depending on the speed and the number of occupants or maximum load in the vehicle.

Reinflating the tires:

When checking tire pressure, it is important to do so when the tires are cold. This means allowing the vehicle to sit for at least three hours to ensure the tires are at the same temperature as the ambient temperature.

To reinflate the tires:

    Check the recommended tire pressure for your vehicle.
    Follow the instructions provided on the air pump and inflate the tire(s) to the correct pressure.
    In the center display of your vehicle, open the "Car status" app.
    Navigate to the "Tire pressure" tab.
    Press the "Calibrate pressure" option and confirm the action.
    Drive the car for a few minutes at a speed above 30 km/h to calibrate the tire pressure.

Note: In some cases, it may be necessary to drive for more than 15 minutes to clear any warning symbols or messages related to tire pressure. If the warnings persist, allow the tires to cool down and repeat the above steps.

Flat Tire:

If you encounter a flat tire while driving, you can temporarily seal the puncture and reinflate the tire using a tire mobility kit. This kit is typically stored under the lining of the luggage area in your vehicle.

Instructions for using the tire mobility kit:

    Open the tailgate or trunk of your vehicle.
    Lift up the lining of the luggage area to access the tire mobility kit.
    Follow the instructions provided with the tire mobility kit to seal the puncture in the tire.
    After using the kit, make sure to securely put it back in its original location.
    Contact AnyCompany or an appropriate service for assistance with disposing of and replacing the used sealant bottle.

Please note that the tire mobility kit is a temporary solution and is designed to allow you to drive for a maximum of 10 minutes or 8 km (whichever comes first) at a maximum speed of 80 km/h. It is advisable to replace the punctured tire or have it repaired by a professional as soon as possible."
}
```

    Example Output:

```textile
```

#### Task 4: Conversational Interface - Chat with Llama 3 and Titan Premier LLMs

###### Task 4-1:

    Mode: ***Chat***

    Model: ***meta.llama3-8b-instruct-v1:0***

    Parameters:

```json
{
    "max_gen_len": 512,
    "temperature": 0,
    "top_p": 1
}
```

    Prompt:

```textile
Hi there!
```

```textile
Give me a few tips on how to start a new garden.
```

```textile
bugs
```

    Input:

    Example Output:

```textile
```

###### Task 4-2:

    Mode: ***Chat***

Model: ***meta.llama3-8b-instruct-v1:0***

    Parameters:

```json
{
}
```

    Prompt:

```textile
R in SageMaker
```

    Input: [Shrinked]Amazon_SageMaker_FAQs.csv

    Example Output:

```textile
```

#### Task 5: Invoke Bedrock model for code generation

    Mode: ***Single prompt***

    Model: ***meta.llama3-8b-instruct-v1:0***

    Parameters:

```json
{
    "max_gen_len": 2048,
    "temperature": 0,
    "top_p": 1
}
```

    Prompt:

```textile
You have a CSV, sales.csv, with columns:
- date (YYYY-MM-DD)
- product_id
- price
- units_sold

Create a python program to analyze the sales data from a CSV file. The program should be able to read the data, and determine below:

- Total revenue for the year
- Total revenue by product 
- The product with the highest revenue 
- The date with the highest revenue and the revenue achieved on that date
- Visualize monthly sales using a bar chart

Ensure the code is syntactically correct, bug-free, optimized, not span multiple lines unnessarily, and prefer to use standard libraries. Return only python code without any surrounding text, explanation or context.
```

    Input: sales.csv

```csv
date,product_id,price,units_sold
2023-01-01,P001,50,20
2023-01-02,P002,60,15
2023-01-03,P001,50,18
2023-01-04,P003,70,30
2023-01-05,P001,50,25
2023-01-06,P002,60,22
2023-01-07,P003,70,24
2023-01-08,P001,50,28
2023-01-09,P002,60,17
2023-01-10,P003,70,29
2023-02-11,P001,50,23
2023-02-12,P002,60,19
2023-02-13,P001,50,21
2023-02-14,P003,70,31
2023-03-15,P001,50,26
2023-03-16,P002,60,20
2023-03-17,P003,70,33
2023-04-18,P001,50,27
2023-04-19,P002,60,18
2023-04-20,P003,70,32
2023-04-21,P001,50,22
2023-04-22,P002,60,16
2023-04-23,P003,70,34
2023-05-24,P001,50,24
2023-05-25,P002,60,21
```

    Example Output:

```textile
```

#### Task 6: Building conversational applications with the Converse API (N/A)

    Mode:

    Model:

    Parameters:

    Prompt:

    Input:

    Example Output:

```textile
```
