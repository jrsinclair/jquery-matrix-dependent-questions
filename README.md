# Matrix Dependent Questions jQuery Plugin

**Make a form question's visibility dependent on some other question simply by adding `data-depends-on="inputName=value"` to a HTML input element. No other code required.**

This plugin allows you to specify that a particular form question should only be
made visible if the answer to a previous question is a specific value. It does this
by making use of HTML5 data attributes. The code is based on the [Dependent Questions jQuery plugin](https://github.com/jrsinclair/jquery-dependent-questions), but has been modified for use with Squiz Matrix Custom Forms (Requires Squiz Matrix version 4.14.2 or greater). For example:

`````html
<form action="?" id="myform">
  <div class="sq-form-question">
    <div class="sq-form-question-title">Would you like to see another question?</div>
    <span>
      <input type="radio" name="q72:q1" value="0" id="q72_q1_0"/>
      <label for="q72_q1_0">No</label>
    </span>
    <span>
      <input type="radio" name="q72:q1" value="1" id="q72_q1_1"/>
      <label for="q72_q1_1">Yes</label>
    </span>
  </div>
  <div class="sq-form-question">
    <label for="extra">What else would you like to add?</label>
    <input type="text" name="q72:q2" id="extra"  data-depends-on="q72:q1=1"/>
  </div>
</form>
`````

In the above example, the question "What else would you like to add?" would only be
displayed when the first question is answered as "yes".

Note that the `data-depends-on` attribute refers to the form input **name**, not an ID.

To use plugin, add something like the following to your web page:

`````html
<script src="http://code.jquery.com/jquery.min.js"></script>
<script src="jquery.matrix-dependent-questions.js"></script>
<script>
  $('#myform').dependentQuestions();
</script>
`````
## Options

You can specify how the dependent questions are revealed by passing options to the plugin constructor. For example, if you would like the questions to fade in, rather than slide down, you could specify something like the following:

`````javascript
$("myform").dependentQuestions({
    effect: "fade",    // This can be 'fade' or 'slide'
    duration: "slow"   // This can be 'slow', 'fast', or a number of milliseconds
});
`````

## Thanks

Development of this plugin was supported by [Squiz](http://squiz.com.au).
