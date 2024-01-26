Code reviews check the results of software engineering. According to IEEE-Norm 729, a review is a more or less planned and structured analysis and evaluation process. Here we distinguish between code review and architect review. 

To perform a code review means that after or during the development one or more reviewer proof-reads the code to find potential errors, potential areas for simplification, or test cases. A code review is a very good opportunity to save costs by fixing issues before the testing phase.

What can a code-review be good for?

* Code quality
* Code clarity and maintainability
* Quality of the overall architecture
* Quality of the documentation
* Quality of the interface specification

For an effective review, the following factors must be considered:

* Definition of clear goals.
* Choice of a suitable person with constructive critical faculties.
* Psychological aspects.
* Selection of the right review techniques.
* Support of the review process from the management.
* Existence of a culture of learning and process optimization. 
 
Requirements for the reviewer: 

* The reviewer must not be the owner of the code.
* Code reviews may be unpleasant for the developer, as he or she could fear that code will be criticized. If the critic is not considerate, the code writer will build up rejection and resistance against code reviews.

Precheck

Developers should complete the following checklist prior to requesting a peer code review.

* Can I answer "Yes" to each of these questions?
  - Did I take time to think about what I wanted to do before doing it?
  - Would I pay for this?
  - Can I defend my work / decisions I made?
* NO sloppiness.
  - Code is well formatted.
  - Code is not duplicated in multiple places.
  - Named variables.
  - Tables have foreign keys (and associated indexes)...
* Run the APEX Advisor (if using APEX).
* Code is well commented.
  - Package specs includes a description of what the procedure does and what the input variables represent.
  - Package body includes comments throughout the code to indicate what is happening.
* The application includes end user help.