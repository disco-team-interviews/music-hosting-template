# Music File Hosting API

Welcome to DISCO's backend technical assessment!

This is a short project followed by a call with two of our engineers, where we'll talk through your code and extend it together.

**Please spend about 2 hours on this.** Incomplete work is completely fine: sketch anything you didn't get to in comments, pseudocode or the notes at the bottom of this file.

When you're done, push your work to your own GitHub repo (an anonymous one is fine) and send us the link.

## What we're looking for

1. Practical, real-world code you'd be happy to ship, not the cleverest one-liners.
2. Awareness of what matters in production: validation, security, performance, observability and testing. If you run out of time, explain how you'd handle these in comments or in your notes.
3. Your own judgement. Whether you use AI tools is entirely up to you. Either way, what we care about is that you understand, and can explain, everything you submit.

## The project

Build a small backend API that lets musicians upload tracks and get back links to them.

1. **Django REST Framework is recommended.** This repo is a starting point with Django and DRF already set up, only there to save you setup time. You're free to change anything in it (project layout, settings, libraries) and you're not locked into any of its choices.
2. **No frontend is needed.** The DRF browsable API, or curl / HTTPie examples, are enough.
3. Skip registration and authentication. Assume users are already logged in (for example, create users through the Django admin and log in to the browsable API).
4. Users can:
   1. Upload a track (MP3 or WAV) via HTTP
   2. List their tracks, including duration and format
5. There are three account tiers:
   1. **Basic:** a link to a 30-second preview clip (MP3, 128 kbps)
   2. **Premium:** the 30-second preview, a full-length MP3 (128 kbps) for streaming, and a link to the originally uploaded file
   3. **Enterprise:** everything in Premium, plus the ability to fetch a link to a previously uploaded track that expires after a number of seconds the user chooses (between 300 and 30000)
6. Cutting and transcoding audio needs something like ffmpeg (for example via pydub). If setting it up eats into your time, stub the processing behind a clear interface and focus on the API.
7. Expiring links: if you run short on time, describe in your notes how you would implement them instead of coding them.

## Getting started

Requires Python 3.12+.

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

Log in at http://127.0.0.1:8000/api-auth/login/ and you'll land on the API root at http://127.0.0.1:8000/api/. The admin is at http://127.0.0.1:8000/admin/.

Run the tests with:

```bash
python manage.py test
```

If you use pydub, you'll need ffmpeg installed (`brew install ffmpeg` or `apt install ffmpeg`). On Python 3.13+ you'll also need `pip install audioop-lts`, because pydub depends on the `audioop` module, which was removed from the standard library.

## The follow-up call

No extra preparation is needed beyond your submission. We'll ask you to walk us through your solution and the choices you made, then take it and evolve it into a larger system, with bigger files, asynchronous processing and external services. There's no single right answer; we're interested in how you reason about trade-offs.

## Your notes

Please fill this in before submitting (one page max).

### How to run it

Anything beyond the "Getting started" steps above.

### Key decisions and trade-offs

Including anything you deliberately left out.

### What you'd do next with more time

### AI tools (only if you used any)

How you used them, including at least one suggestion you changed or rejected, and why. If you didn't use any, skip this section.
