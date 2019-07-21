# Christophe Pettus - PostgreSQL Experts - Humans do not have a primary key
thebuild.com

Start new project -> start writing SQL

Add SQL table for customer

Primary Key + first name + middle initial + last name ....

^ doesn't work - languages and cultures have different naming schemes!

Hungarian very unique, apparently mix things up

Icelandic names do not have a family name - "last name" is "child of <father's name>"

Indonesia - only one name

Fine -> given name and optional other name

But two last names or more!

"Given" name is kinda weird anyways - Madonna, Cher

So... just have a name field!

`Dear <Felipe Grecia>` < king of spain, so we have to add a title

and then we might have to add a bajillion title options! (German countries can have multiple Dr.s in their titles)

So... why are we doing this?  We should just ask "What should we call you?"

Niantic Harry Potter game restricts acceptable names (Josh Gay's legal name Josh Gay was not permitted)

FB limits number of capitals you can have in your name

But these things can be valid!

w3.org/International/questions/qa-personal-names

So... one "what should we call you?" field?!

Credit card applications want a first and last name.

So, clarify: "as appears on passport", etc


Gender associated items, so we need to track that!

Add gender field that takes on char, make sure we validate M, F, or O

Stop this is terrible.

"marketing analytics is another name for 'curiosity'"

Fraught question to ask anyways, so why ask...

linuxmafia.com/kb/Essays/marriage.html


We should have family plans for our aluminum siding!

Mother, father, done

But... orphans!

Okay, make optional

Parent 1 and parent 2

But, remarriage? Add parent 3!

Eh... okay have a many to many table with a duration and relationship name

Stop this is terrible.

Sony tried a family plan for PlayStation, so people gamed it

So they changed to everyone has to live in same house 

Divorced parents, child has to decide which parent to share with

So, why have this?  Business reason, so let's not.


Date of birth often required

Why have this?  For age/demographic? Can just ask for a range.  Don't make DOB a security question....

Stop this is terrible.


Social network for families

Had a text box for child's prescriptions... uh oh!  HIPAA!  And GDPR!

Stop this is terrible.

If you don't block EU, have to be GDPR compliant

So... don't ask for things you don't need to!  Solicitation is what makes you need to be compliant

Rules:
1. Personal experience is worthless.  Your experience is pretty narrow, so don't know how to include people with different family structures or cultural backgrounds
2. Under-model.  Don't make it all rigid.  Let the computer sort it out, people can sort out their own lives
3. Under-collect.  Don't need additional complexity that can break things.
4. Over-communicate with customer.  Tell why collecting the info
5. Focus on the core need.  Why do you need this?

Audience Q: How to handle people being duplicated?

There's not really any way to uniquely identify people.  See: social security.  Once you can uniquely identify a person, identity theft is possible.  HIPAA prescribes that no two healthcare systems can use the same identifier.  Again, ask why/use case.  Credit card company deal: just say one account per credit card or something.  Data scientists want really clean data tho.  Once at war w/ customers over their data, should just give up.

Addresses can also be pretty problematic.  In EU, can just wave a thick GDPR printout and wave it at them when asking them to fix something.