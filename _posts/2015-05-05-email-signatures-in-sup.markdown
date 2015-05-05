---
layout: post
title: "Email signatures in Sup"
date: 2015-05-05T12:41:50-04:00
---

I'm a big fan of the [Sup](http://supmua.org/) email client. I've been
using it for around a year now, and I only just recently realized I didn't
have my email signatures properly configured! I had a little trouble
getting it to work correctly so I thought I would outline the process
here.

Sup provides a handy way to write a script to handle attaching signatures
to messages. In my case I use three different email addresses to send mail
on my machine, so I wanted to have the signature change depending on which
address was in the 'from' field (so as to adjust to different levels of
formality, etc).

This is pretty easy to do! This is what my `signature.rb` file looks like:

    {% highlight ruby %}
    if from_email == 'alice.writes.wrongs@gmail.com'
        "~*~ alice ~*~
    Public PGP key: https://pgp.mit.edu/pks/lookup?op=get&search=0xB3580CB0CD99F2A4
    PGP fingerprint: 4B57 95AF E3F3 404A 46C2 2932 B358 0CB0 CD99 F2A4"
    elsif from_email == 'axyridis@riseup.net'
        "AR
    Public PGP key: https://pgp.mit.edu/pks/lookup?op=get&search=0x3D47670F42269A83
    PGP fingerprint: 43D1 4BEF 39F7 4027 B02A DC4D 3D47 670F 4226 9A83"
    else
        nil
    end
    {% endhighlight %}

which handles it pretty nicely! I've also set mine up the include the PGP
key that is relevant to the particular email address in question.

Happy supping!
