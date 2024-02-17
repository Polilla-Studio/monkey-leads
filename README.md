Integration of Monkey Leads
-

In the form on your website, you need to include

**Required in the form**

- data-request="onCatchLead" *To include the MonkeyLeads watcher*

**Optional in the form:**

- data-request-validate *To validate fields on submission*
- data-request-flash *Used to display messages to users in flash format*

**Optional on the button**

- data-attach-loading *to lock and show a loader when submitting the form*


```
<form data-request="onCatchLead"
    data-request-validate
    data-request-flash>
    <div class="row gtr-uniform gtr-50">
        <div class="col-6 col-12-xsmall">
            <input type="text" name="name" id="name" placeholder="Name" />
            <!-- Be sure to include a validation tag for the field -->
            <div data-validate-for="name"></div>
        </div>
        <div class="col-6 col-12-xsmall">
            <input type="email" name="email" id="email" placeholder="Email" />
            <div data-validate-for="email"></div>
        </div>
        <div class="col-6 col-12-xsmall">
            <input type="hidden" name="origin" id="origin" value="home-form" />
        </div>
        <div class="col-12">
            <textarea name="message" id="message" placeholder="Message" rows="4"></textarea>
            <div data-validate-for="message"></div>
        </div>
    </div>
    <br />
    <ul class="actions">
        <li>
            <button class="button primary" data-attach-loading>Send Message</button>
        </li>
    </ul>
</form>
```

It is also possible to add some extra parameters in the form to define validation rules

```
data-request-data="rules: 'terms|accepted, company|required, updates|accepted'"
```
 
And we have included a function to clear the form once it has been sent

```
data-request-success="monclean()" 
```

Monkey Leads has the capability to adapt to any form you have on your website, and you can find an example of implementation in the default markup of the CatchLead component.

The inputs that are natively registered are 
Name, Last Name, Email, Telephone, and origin of the lead. In the component's configuration, you only need to specify the name of the input that corresponds to each of these data. For example, if your form has this structure (it is very simplified for the example):

 ```
<form>
    <input type="text" name="name-lead" id="name" placeholder="Name" />
    <input type="text" name="last-name-lead" id="last-name" placeholder="Last Name" />
    <input type="email" name="email-lead" id="email" placeholder="Email" />
    <input type="hidden" name="origin-of-the-lead" id="origin" value="budget-request" />
    <label for="contact-reason">Reason for contact</label>
    <select name="contact-reason" id="contact-reason">
        <option value="i-have-a-question" >Question</option>
        <option value="just-say-hello" selected>Just say Hello</option>
        <option value="can-i-get-your-number">Can I get your number?</option>
    </select>
    <textarea name="message" id="message" placeholder="Message" rows="4"></textarea>
    <button class="button primary">Send</button>
</form>
 ```
 
In the component configuration, the following data goes:

```
[catchLead]
name = "name-lead"
last_name = "last-name-lead"
email = "email-lead"
telephone = ""
origin = "budget-request"
extra_data = "contact-reason,message"
```
