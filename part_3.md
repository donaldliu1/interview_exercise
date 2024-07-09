## 1. How would you go about implementing the solution
# Conversation
- Currently tags are implemented but only to conversation
- Current schema for conversation has tag field
- When POST conversation you have a string where you can enter the tag
- You can PUT to edit the tag currently (/conversation/{conversationId}/tags)
- 

# Message
- Reuse the way tags are implemented in conversation but to message
- Change message schema to include a tag field for messages
- When POST message allow user to add tags 
- If message exists and user wants to add, edit or more use PUT, currently messageID exists so we could use that to target the specific message (/conversation/{conversationId}/{messageID}/tags)
- Allow users to GET messages in a conversation using a query that matches anything that has that string

## 2. What problems you might encounter
- IF users are allowed to enter their own tags rather than pre-defined ones, possiblity of injection attacks/XSS
- Database performance could be impacted if there is large amount of tags/messages with tags
- Database performance could be impacted by the new increase of queries
- Designing a intuitative UX/UI for the new message tag system and search function
- IF multiple users have permission to edit tags on messages could cause conflict
- Using tags to bypass any profanity filters

## 3. How would you go about testing
- Currently tests are ran with spec.ts files, in several of the conversation files there are multiple unit tests which test updating the tags, could reuse this to work with messages

- Injection testing       Use automated tools to check for SQL injection vulnerabilites (SQLMap)
- XSS testing             Same as injection testing for automated tool for XSS vulnerabilites (OWASP ZAP)
- Unit testing            Test functions of the code for example testing that the tag does not contain a list of profanity and is sanitised
- API testing             Test that API endpoints are performing as expected such as sending a GET request and defining what is expected as a response
- Integration testings    Test components working together such as adding tags and retrieving them
- End-to-End testing      Test front end to back end, such as clicking a button to add tags in the user interface and checking if the tag is correctly added in the database
- Performance testing     Test system performance under load 
- Acessibility tesing     Test for accessibility, could use a tool like lighthouse which audits the page

## 4. What I've implemented
I'm having a hard time understanding all the code to fully implement the idea that I want, however I was able to:
- Add a new field in message section of openai.json, similar to conversation section of openai.json
- Updated the schema for the new tag


