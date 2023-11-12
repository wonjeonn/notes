# Week 9: HTML5 Forms and CSS Styling

## HTML5 Forms

### Basics of HTML Forms

- HTML forms provide a way for users to input data on a web page.
- The `<form>` element is the foundation for creating forms and represents a section of a web page containing interactive controls.
  
  ```html
  <form id="data" action="/submit" method="post">
    <!-- Form controls go here -->
  </form>
  ```

- The `action` attribute in `<form>` specifies the URL where the data should be sent and `method` defines the HTTP method for submitting data (default is GET).
- `<input>` is a common form control. Example:

  ```html
  <input id="name" type="text" name="first-name">
  ```

### Form Example 1: Google Search

- Google's search form uses `<form>` with various `<input>` elements.
- Hidden inputs (`type="hidden"`) store data not visible to the user but submitted with the form.

    ```html
    <form id="tsf" class="tsf nj" action="/search" method="GET" name="f">
        <input name="source" type="hidden" value="hp">
        <input value="qIXxW6O0FeTMjwT1zpioCA" name="ei" type="hidden">
        <input class="gLFyf gsfi" maxlength="2048" name="q" type="text" title="Search">
        <input value="Google Search" name="btnK" type="submit">
        <input value="I'm Feeling Lucky" name="btnI" type="submit">
    </form>
    ```

### Form Example 2: Login

- Login form uses `<label>` for text labels, `<input>` for text and password input and `<form>` with `method="POST"`.

    ```html
    <form action="/webapps/login" method="POST" name="login">
        <label for="user_id">Username</label>
        <input id="user_id" type="text" name="user_id" size="25" maxlength="50">

        <label for="password">Password</label>
        <input id="password" type="password" name="password" autocomplete="off" size="25">

        <input id="entry-login" type="submit" class="button expand" value="Login" name="login">
        <input type="hidden" name="action" value="login">
        <input type="hidden" name="new_loc" value="">
    </form>
    ```

### Form Example 3: Twitter Email Notification Settings

- Twitter's form uses checkboxes and `<select>` (dropdown) for user preferences.

    ```html
    <form id="notifications-form" method="POST" action="/settings/email_notifications/update">
        <fieldset class="control-group">
            <legend class="control-label">Email me when</legend>
            <label class="t1-label checkbox">
                <input type="checkbox" value="1" id="send_network_activity_email" name="user[send_network_activity_email]" disabled="">
                You have new notifications.
                <a href="https://support.twitter.com/articles/127860#tweet-activity" target="_blank" class="learn-more" rel="noopener">Learn more.</a>
            </label>
            <input type="hidden" value="0" name="user[send_network_activity_email]" disabled="">
            <label class="t1-label checkbox">
                <input type="checkbox" value="1" id="send_new_direct_text_email" name="user[send_new_direct_text_email]" disabled="">You're sent a direct message
            </label>
            <input type="hidden" value="0" name="user[send_new_direct_text_email]" disabled="">
            <label class="t1-label checkbox">
                <input type="checkbox" value="1" id="send_shared_tweet_email" name="user[send_shared_tweet_email]" checked="" disabled="">Someone emails a Tweet to you
            </label>
            <input type="hidden" value="0" name="user[send_shared_tweet_email]" disabled="">
        </fieldset>

        <hr>

        <fieldset class="control-group">
            <legend class="control-label">Email you with</legend>
            <label class="t1-label checkbox">
                <input type="checkbox" value="4" id="network_digest_schedule" name="user[network_digest_schedule]" disabled="">Top Tweets and Stories
            </label>
            <label class="t1-label">
            <span class="u-hiddenVisually">Preference</span>
            <select class="t1-select preference-dropdown" disabled="">
                <option value="1">Sent daily</option>
                <option value="3">Sent weekly</option>
                <option value="4" selected="selected">Sent periodically</option>
            </select>
            </label>
            <input type="hidden" value="0" name="user[network_digest_schedule]" disabled="">

            <label class="t1-label checkbox">
                <input type="checkbox" value="3" id="performance_digest_schedule" name="user[performance_digest_schedule]" checked="" disabled="">Updates about the performance of your Tweets
            </label>
            <input type="hidden" value="0" name="user[performance_digest_schedule]" disabled="">
        </fieldset>
    </form>
    ```

### Form Example 4: Airbnb Search

- Airbnb's search form uses `<button>` for custom buttons and introduces new attributes like `autocomplete` and `placeholder`.

    ```html
    <form id="MagicCarpetSearchBar" action="/s">
        <label class="_rin72m" for="magic-carpet-koan-search-bar">WHERE</label>
        <input type="text" class="_1wl3axt0" autocomplete="off" autocorrect="off" spellcheck="false" id="Koan-magic-carpet-koan-search-bar__input" name="query" placeholder="Anywhere" value="">
        
        <label class="_rin72m" for="checkin_input">CHECK IN</label>
        <input type="text" class="_14fdu48d" id="checkin_input" name="checkin" placeholder="dd-mm-yyyy" value="" readonly="">
        
        <label class="_rin72m" for="checkout_input">CHECK OUT</label>
        <input type="text" class="_14fdu48d" id="checkout_input" name="checkout" placeholder="dd-mm-yyyy" value="" readonly="">
        
        <label class="_rin72m" for="lp-guestpicker">GUESTS</label>
        <button class="_1nil34o" type="button">Guests</button>
        
        <button type="submit" class="_2giblnw">Search</button>
    </form>
    ```

### Form Example 5: Google Translate

- Google Translate form includes a `<textarea>` for multiline text and `<input type="file">` for file uploads.

    ```html
    <form id="gt-form" action="/" name="text_form" method="post" enctype="multipart/form-data">
        <input type="hidden" id="gt-sl" name="sl" value="auto">
        <input type="hidden" id="gt-tl" name="tl" value="es">
        <input type="hidden" name="js" value="y" id="js">
        <input type="hidden" name="prev" value="_t" id="prev">
        <input type="hidden" name="hl" value="en" id="hl">
        <input type="hidden" name="ie" value="UTF-8">
        
        <textarea id="source-is" name="text-is" disabled="" dir="ltr" spellcheck="false" autocapitalize="off" autocomplete="off" autocorrect="off" class="goog-textarea short_text" wrap="SOFT"></textarea>
            
        <input type="file" name="file" id="file" size="40">
    </form>
    ```

## Leveraging the Platform: Choosing the Right Control

### Input Types for Specific Data:

- `<input type="tel">`: For telephone numbers. On mobile, it displays a keypad-style entry.

- `<input type="url">`: For URLs. On mobile, it offers extra buttons (e.g., .com) for easier URL entry.

- `<input type="email">`: For email addresses. On mobile, it includes keys like @ to facilitate email address entry.

- `<input type="number">`: For integers. On mobile, the keyboard switches to the number pad.

- `<input type="range">`: For a number between two values, displayed as a slider for easy value selection.

- `<input type="date">`, `<input type="time">`, `<input type="week">`, `<input type="month">`, `<input type="date-local">`: For date/time values, providing special-purpose controls for valid date and time entry.

- `<input type="color">`: For color values, with the OS providing a color picker control.

### Leveraging Autocomplete and Name Attributes:

- Browsers autofill common field information.

  ```html
  <label for="username">Username</label>
  <input type="text" name="username" id="username" autocomplete="username">
  ```

  ```html
  <label for="mobile-num">Mobile Number</label>
  <input type="tel" name="mobile" autocomplete="tel" id="mobile-num">
  ```

### Other `<input>` Attributes:

- **`autofocus`:** If present, indicates that the input should automatically gain focus.

- **`required`:** If present, indicates that the input must have a value before form submission.

- **`tabindex`:** A number indicating the order in which controls receive focus during keyboard navigation.

- **`list`:** Refers to the id of a `<datalist>` element providing autocomplete suggestions.

  ```html
  <input type="text" list="subjects" name="course">
  <datalist id="subjects">
    <option value="EAC150">
    <option value="IPC144">
    <option value="ULI101">
    <option value="IOS110">
  </datalist>
  ```

## Forms and CSS

### Applying Consistent Styling:

- Apply the box-sizing property to even out inconsistencies between different controls:
  ```css
  input, textarea, select, button {
    width: 150px;
    margin: 0;
    box-sizing: border-box;
  }
  ```

- Style `<label>` for proper alignment:
  ```css
  label {
    display: inline-block;
    width: 100px;
    text-align: right;
  }
  ```

### CSS Selectors and Forms

#### Targeting Specific Form Controls:

- **Attribute Selector:**
  - Match based on the presence or exact/partial match of an attribute's value.

  ```css
  /* Style submit input controls */
  input[type="submit"] {
      border: 2px solid #ccc;
  }
  ```

- **Sibling Selectors:**
  - Style based on the relationship with other elements.

  ```css
  /* Style all <input> elements that are direct siblings of a <label> */
  label+input {
      /* ... */
  }

  /* Style all <input> elements that are siblings (direct or indirect) of a <label> */
  label~input {
      /* ... */
  }
  ```

- **Pseudo-Selectors for Form Control States:**
  - Style based on the state of a form control.

  ```css
  :valid, :invalid, :required, :optional, :in-range, :out-of-range {
    /* Style based on form control state */
  }
  ```
