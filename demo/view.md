# Build the view

Starting with the layout, get more stuff in there to make this work correctly

```
meta(charset='utf-8')
meta(http-equiv='X-UA-Compatible', content='IE=edge')
meta(name='description', content='#{description}')
meta(name='viewport', content='width=device-width, initial-scale=1.0, minimum-scale=0.5 maximum-scale=1.0 minimal-ui')
```

Update the `index.js` file in `./routes`

```
res.render('index', { title: 'Contact me', description: 'This is a new demo' });
```

Open `./views/index.jade` and add the following:

```
section.message-container
  h1.title= title
  form#form.form(action='#', method='get')
    ul
      li
        label(for='name') Your Name:
        input#name(type='text', placeholder='Your Name', name='name', tabindex='1')
      li
        label(for='email') Your Email:
        input#email(type='email', placeholder='Your Email', name='email', tabindex='2')
      li
        label(for='message') Message:
        textarea#message(placeholder='Message…', name='message', tabindex='3')

    button#submit Send Message
```
