# PhonePairing

Expiring phone pairing: a one-time QR code with a visible countdown and a plain statement of what the phone will get.

**Consumer provides:** a `cs-card` with the generated `cs-qr` (always dark modules on white, in both themes, because scanners need it), a `cs-countdown` that is announced at 1 minute and at expiry rather than every second, the scope sentence, and New code / Cancel.

- Expired codes are replaced by "Code expired" and New code. Never leave a stale QR on screen.
- After pairing, the phone appears in `ParticipantRoster` under your name as "Phone · paired 20:52 ET" with Unpair.
- The QR here is a stand-in; the real code is generated per session.
