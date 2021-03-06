# Validation

Whenever you accept input from a visitor, that input needs to be validated.

Here are examples of the kind of validation you may see on Project 2:

+ Scrabble calculator: An input asking for the word should only accept letters.
    + Pass: `apple`, `garage`
    + Fail: `-1`, `99`, `0range`
+ Password generator: An input asking for the password length should have a reasonable range like 1 to 10. It should also only allow positive integers.
    + Pass: `1`, `5`, `10`
    + Fail: `-1`, `abc`, `99`

Here are examples of validations you might see in a real world application:

+ An email input in a sign-up form should a) confirm it's a valid email address and b) the email address does not already exist in the system.
+ An input collecting a US zip code should have a min/max of 5 characters and only contain numbers
+ An input collecting a discount code should confirm the code is valid and not expired
+ etc...

Ultimately, validation should happen on both the client (via HTML + JavaScript) *and* the server (PHP).

The &ldquo;first-pass&rdquo; client-side validation via HTML and JavaScript can be used to give the visitor instant feedback about many issues and prevent form submission.

(Sometimes, the client-side validation may send a request to the server using Ajax to confirm data, e.g username does not already exist).

Once client-side validation passes, the form can submit to the server where a second-pass validation is done.

This second-pass validation step is necessary when working with important data because it's possible for users to bypass client-side validation using browser web inspector tools.

In this course, because our focus is on the server end of things, client-side validation is *optional*. It's not as optimal as having both, but it gets the job done for our purposes.

If interested, there is some &ldquo;low hanging fruit&rdquo; in terms of client-side validation via HTML5 validation attributes like `required`, `min`, `max`, `email`, etc. [You can learn more about these attributes here.](https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/Data_form_validation) Again, this type of validation is *not* required for projects in this course.

## Server-side validation

Goals:
+ Validation should happen in your logic file, before that data is used.
+ If there are errors in the form data, the visitor should be directed back to the form where the errors occurred.
+ Errors should stand-out from the rest of the page so they're not easily missed. By convention, error messages should be some shade of red. 
+ Any fields that had errors should be pre-filled with the problematic data the user had entered, making it easy for them to correct the problems. Exceptions are made for secure fields like passwords, credit card numbers, etc.

To accomplish these goals in P2, we'll use a PHP class I'm providing called `Form.php` which includes validation functionality in addition to some other form-related utilities.

Documentation for this class is provided in the next note set: 