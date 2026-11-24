# 5. Connect the contact form

Portfolio & Agency Site Template by The Diamond Empire, https://thedempire.shop/

The contact form on `/contact/` is a demo until you connect it. It checks what the visitor typed, shows clear error messages, and then shows a confirmation that is marked "Demo" and says that nothing was sent. It makes no network request. Do not publish the site with the demo form.

## How the form works

1. The visitor fills in name, email, topic, message and a permission checkbox.
2. The form checks the values (`src/lib/contact/validate.ts`) and shows an error summary and a message under each field that needs fixing.
3. When the values are valid, the form passes them to one function, `submitContact`, defined in `src/lib/contact/adapter.ts`.
4. That function returns `{ ok: true }` or `{ ok: false }`, and the form shows the matching message.

The form stays switched off until the page's JavaScript has loaded, so a message can never be sent as an ordinary page request (which would put it in the address bar). Without JavaScript it says to email you instead.

## Connecting a service

Open `src/lib/contact/adapter.ts`. It contains one line that chooses the adapter. Replace it with an adapter that sends the message where you want it. A ready-made one that posts JSON to an address you choose is in `src/lib/contact/http-adapter.ts`:

```text
import { createJsonPostAdapter } from './http-adapter';
export const submitContact = createJsonPostAdapter('https://forms.your-provider.example/your-form-id');
```

Check what your provider expects (field names, headers, spam protection) and what its privacy terms say. The address must use `https://`.

## Before you publish

- Send yourself a real test message and check that it arrives.
- Validate the data again on the server that receives it, and use your provider's spam protection. The checks in the browser are a convenience, not security.
- Name the provider in your privacy notice: the visitor's message leaves their device when the form is connected.
- Update the confirmation text in `src/components/ContactForm.tsx` if "within two working days" is not what you promise.
