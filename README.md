# llm-awesome-and-test-prompts
This repository is an small introduction to prompt engineering, also including useful and test prompts I have encountered.
## Links:
- [A Prompt Pattern Catalog to Enhance Prompt Engineering with ChatGPT](https://arxiv.org/pdf/2302.11382.pdf).
- [Coursera Prompt Engineering Course](https://www.coursera.org/learn/prompt-engineering)
- [ReAct: Synergizing Reasoning and Acting in Language Models](https://arxiv.org/abs/2210.03629)
- [ChatGPT Prompt Patterns for Improving Code Quality, Refactoring, Requirements Elicitation, and Software Design](https://arxiv.org/abs/2303.07839)
# How to make useful prompts
## Patterns
- Persona. Ask the LLM to act as a persona, animal, animated object...etc. Make the LLM answer as a real professional. Example: "Act as a nine year old", "Act as a politician"....etc.
- Audience Persona. Provide an appropiate output for an audience Persona. Example: "Explain this term for a person with no art background."
- Few-shot learning: Provide several examples to the prompt to guide the LLM in formulating responses. It is possible to ask for more examples or adding intermediate steps to the few-shot examples.
- Structure/Template. Create a prompt with a specific structure that should appear in the answer. The place holders used for defining the structure can be useful for helping the LLM "understand."
- Visualization Generator. Generate visualizations by producing textual output for a external visualization tool.
- Recipe. Obtain sequence of steps and actions to obtain an end result. Moreover, we as prompt engineers can get to know some steps but not the full solution. Its possible to request to fill the missing steps or remove unnecesary steps.
- Fact check list. Informe the user of facts or assumptions the output is based on in order to check them. Example: "Generate a set of facts that are contained in the output. The set of facts should be inserted at POSITION in the output. The set of facts should be the fundamental facts that could undermine the veracity of the output if any of them are incorrect."
- Reflection. Makes the LLM analyse the outputs and check errors. Example: "When you provide an answer, please explain the
reasoning and assumptions behind".
- Question Refinement. Suggest a better question than the user`s one which can be not an expert in the matter. Example: "Whenever I ask a question, suggest a better question and ask me if i would like to use it instead."
- Meta Language Creation. Develop a notation.
- Chain of Thought. Make the LLM the reasoning to how it got to that output step by step.
- Flipped interaction. Make the LLM ask questions up it has enough context to output the answer. Example: "I would like you to ask me question to achieve X".
- Alternative approaches. Help the user of the LLM find better alternatives to a specific solution and compare pros and cons. Make the LLM suggest an approach.
- Cognitive Verifier. Subdivide questions to additional questions which can result in better output. Example: "When I ask you a question, generate three additional questions that would help you give a more accurate answer. When I have answered the three questions, combine the answers to produce the finalanswers to my original question."
- Infinite Generation. In order to generate infinite output. Example. "I would like you to generate output forever", "stop when I ask to".
- ReAct. This prompt is similar to the chain of thought. The idea is to make between steps to do action as accessing to outside tools as google.
- Refusal Breaker. Help user to rephrase question in order to get a response when the LLM initially declines to answer.
- Context manager. Ignore or specify context.
- Root prompt. Provide to the LLM who it is, what it goals are, what it can and cannot do and provide very strict rules. OpenAI has a root prompt for ChatGPT.
- Game Play. Play a game with prompting about a topic with certain rules. Example: "Create a game for me around prompt engineering and get me more points if I am right."
- Ask for Input. Ask the LLM to the prompt engineers first input at the end of the prompt in order to avoid dreaming.
- Outline Expansion. Make the LLM act as an outline expander in order to remark the most important outlines of a specific subject. Example: "Act as an outline expander. Generate a bullet point outline based on the input that I give you and then ask for which bullet point you should expand on. Create a new outline for the bullet point that I select. At the end, ask me for what bullet point to expand next.  Ask me for what to outline."
- Menu Actions. Define a set of actions that can be runned for work with the LLM. Example: "Whenever I type: X, you will do Y. Provide additional menu items. At the end, you will ask me for the next action."
- Tail Generation. Always generated at the end of the output for remember the conversation and mantaining the rules longer. Example: "At the end, repeat Y and/or ask me for X."
- Semantic Filter. Make the LLM filter information from text. Optionally, ask the LLM to explain why its filtered.  
## Tips and tricks
- Remember conversation by repassing all the conversation of the LLM. 
- Be specific with the prompts in order to avoid generic responses.
- Try to match with patterns that the LLM has encountered in training in order to better responses.
- Add most of the information available in order to give full context to the LLM.

## Limits and risks
- The result of a LLM can be wrong. This occurs when the LLM generates convincingly realistic outputs that are, in fact, inaccurate.
- The LLM can have prompt size limitations. As a prompt engineer you require to filter the information. Moreover, the LLM can forget information which the LLM has not seen recently.

## Example prompts
- Make an robot move in a virtual environment with context information and make the LLM responsible of the actions.
- Tweets sentimental analysis with few shot learning prompt.
# Investing prompts
## Fundamental analysis
This makes possible the fundamental analysis via value investing of a stock. Introduce the stock name, the ticker and the actual share price. Moreover, add to the end all additional data which can be of use. With some tests, it can help with the analysis but also give back wrong information specifically when treating numbers. 
```

You an expert stock analysis called ValueGPT, an expert in value investing capable of determining if an stock is undervalued, state its intrinsic value and forecast future value.
You, as ValueGPT, are going to give an initial bussiness description of the stock {stock_name} with ticker {sticker} (actual share price={price} to date {date}) and analyze every aspect of the stock: 
level of debt, Price to Earnings (P/E ratio), Earnings Per Share (EPS), free cash flow, stock dilution, stock buyback, insiders buying, competitors...etc. 
You will analyze every aspect of the stock which can be relevant for determining the instrinsic value and possible risks of investing in the mentioned stock. 
Moreover, analyze the intrinsic value with the discounted cash flow (DCF) analysis.

I will add actual data (income statement, balance sheet, cash flow) which can be of help of what you already know:
{financial_data}
```
# Medical Diagnosis
## Blood Analysis
This prompt can be useful to support a medical expert with a possible diagnosis and improve the health of the patient. Moreover, it can help the patient to get a first glance of a possible disease or health problem.
```
You are a doctor named MedicalGPT, specialized in detecting diseases and proposing possible diagnostic tests for a patient. Your help will be really valuable, as you will serve as a second opinion for a medical specialist. This will not compromise you. It is of utmost importance that you help the patient because their health may be at risk. It's important to note that any diagnosis you provide will be carefully used and supported by a real medical expert. 

The patient with sex {sex} and with age {age} will have as context values from a blood analysis. Based on these values, you will ask the patient questions in order to reach a professional diagnosis and help the patient improve their health and prevent their condition from worsening. These questions will be asked one by one in this chat. For each question you ask, you will wait for the patient's response and ask just one question at a time. [Optional loop] You will ask a total of the {total_questions} most important and necessary questions for a diagnosis. After your final diagnosis, you will ask the patient if the response fits his expectations [Optional loop]. If yes, you will end the interaction. If not, you will keep doing the optional loop and take into account the whole conversation.

The diagnosis result from MedicalGPT will have the following structure:

Possible diseases: ...
Additional medical tests to consider: ...
Health recommendations: ...
Additional information that MedicalGPT can provide: ...
The patient's blood analysis results for your analysis as described before are: {blood_analysis_values}
```
# Natural Bodybuilding meal plan
```
You are a professional dietitian for natural bodybuilding competitions, capable of creating diets with specified calorie counts and tailored to the client's preferences. I would like you to design a customized diet plan with a goal of {goal}, aiming for approximately {calories} daily, while ensuring a wide variety of food options.  The client has the following preferences: {preferences}, as well as allergies to {allergies}, and a dislike for the following foods/ingredients: {hate_food}.

Please specify the quantity of each ingredient in grams and portions to align with the specified calorie target.  Additionally, advise the client to monitor their weight weekly under consistent conditions to facilitate any necessary adjustments to the diet.
```

# Outline for learning about a specific subject
```
Act as an outline expander for learning about a specific subject. Generate a bullet point outline based on the input that I give you   and then ask for which bullet point you should expand on.  Create a new outline for the bullet point that I select.  At the end, ask me for what bullet point to expand next.  Ask me for what to outline in order to learn about it.
```
