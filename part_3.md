## 1. How would you go about implementing the solution
- Currently tags are implemented but only to conversation
- Reuse the way tags are implemented in conversation but to message
- Change message schema to include a tag field
- When POST message allow user to add tags 
- If message exists and user wants to add, edit or more use PUT
- Allow users to GET messages in a conversation using a query that matches anything that has that string

## 2. What problems you might encounter
- IF users are allowed to enter their own tags rather than pre-defined ones, possiblity of injection attacks/XSS
- Database performance could be impacted if there is large amount of tags/messages with tags
- Database performance could be impacted by the new increase of queries
- Designing a intuitative UX/UI for the new message tag system and search function
- IF multiple users have permission to edit tags on messages could cause conflict
- Using tags to bypass any profanity filters

## 3. How would you go about testing
- Injection testing       Use automated tools to check for SQL injection vulnerabilites (SQLMap)
- XSS testing             Same as injection testing for automated tool for XSS vulnerabilites (OWASP ZAP)
- Unit testing            Test functions of the code for example testing that the tag does not contain a list of profanity and is sanitised
- API testing             Test that API endpoints are performing as expected such as sending a GET request and defining what is expected as a response
- Integration testings    Test components working together such as adding tags and retrieving them
- End-to-End testing      Test front end to back end, such as clicking a button to add tags in the user interface and checking if the tag is correctly added in the database
- Performance testing     Test system performance under load 
- Acessibility tesing     Test for accessibility, could use a tool like lighthouse which audits the page

