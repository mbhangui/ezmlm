# ezmlm
ezmlm fork with support for IndiMail multi queue

ezmlm is an easy-to-use, high-speed mailing list manager for qmail.
ezmlm lets users set up their own mailing lists within qmail's address hierarchy. A user, Joe, types ``ezmlm-make ~/SOS ~/.qmail-sos joe-sos isp.net'' and instantly has a functioning mailing list, joe-sos@isp.net, with all relevant information stored in a new ~/SOS directory.

ezmlm sets up joe-sos-subscribe and joe-sos-unsubscribe for automatic processing of subscription and unsubscription requests. Any message to joe-sos-subscribe will work; Joe doesn't have to explain any tricky command formats. ezmlm will send back instructions if a subscriber sends a message to joe-sos-request or joe-sos-help.

ezmlm automatically archives new messages. Messages are labelled with sequence numbers; a subscriber can fetch message 123 by sending mail to joe-sos-get.123. The archive format supports fast message retrieval even when there are thousands of messages.

ezmlm takes advantage of qmail's VERPs to reliably determine the recipient address and message number for every incoming bounce message. It waits ten days and then sends the subscriber a list of message numbers that bounced. If that warning bounces, ezmlm sends a probe; if the probe bounces, ezmlm automatically removes the subscriber from the mailing list.

ezmlm is easy for users to control. Joe can edit ~/SOS/text/* to change any of the administrative messages sent to subscribers. He can remove ~/SOS/public and ~/SOS/archived to disable automatic subscription and archiving. He can put his own address into ~/SOS/editor to set up a moderated mailing list. He can edit ~/SOS/{headeradd,headerremove} to control outgoing headers. ezmlm has several utilities to manually inspect and manage mailing lists.

ezmlm uses Delivered-To to stop forwarding loops, Mailing-List to protect other mailing lists against false subscription requests, and real cryptographic cookies to protect normal users against false subscription requests. ezmlm can also be used for a sublist, redistributing messages from another list.

ezmlm is reliable, even in the face of system crashes. It writes each new subscription and each new message safely to disk before it reports success to qmail.

ezmlm doesn't mind huge mailing lists. Lists don't even have to fit into memory. ezmlm hashes the subscription list into a set of independent files so that it can handle subscription requests quickly. ezmlm uses qmail for blazingly fast parallel SMTP deliveries.
