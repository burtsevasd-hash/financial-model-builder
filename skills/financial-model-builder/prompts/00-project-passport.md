# Step 0. Project passport

Write the output in the language of the user's request.

## Prompt 0.1. Build the passport from the client brief

```
I am a finance professional. A client has asked me for a financial model. We will build it in the project folder attached. Fill in the project passport from the client brief, which is in the folder as a text file.

The passport has seven fields:
1. Business and format
2. Location: country, region, city, type of location
3. Scale
4. Purpose of the model and its audience
5. Horizon and granularity
6. Currency and tax jurisdiction
7. What is already known

Do this:
1. Fill the fields the brief answers. One or two sentences each, no speculation.
2. For every field the brief does not answer, ask me one precise question. Word it so that I can forward it to the client as written.
3. For horizon and granularity propose a default for a business of this kind and explain in one sentence why.
4. For currency and tax jurisdiction, state the country and the currency, and list the legal forms a business of this size usually takes there. Do not research the tax rules yet, that is step 3.

Output the passport as a table: Field | Value | Source (client brief / to clarify / proposed default). Save it to the project folder as «Project passport», named in the language of this project.
```

If there is no written brief, ask for it in any form: an email, a call transcript, meeting notes.
