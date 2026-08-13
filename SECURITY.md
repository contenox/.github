# Security policy

Applies to every repository in the `contenox` organisation, and to the hosted
service at `app.contenox.com`.

## Reporting a vulnerability

Write to **hello@contenox.com** with `Security` in the subject. Describe what
you found and how to reproduce it.

- Receipt acknowledged within **3 working days**.
- A first assessment within **10 working days**.
- We say when a fix is planned as soon as we know — and equally, if we are not
  going to act, we say so and why.

We do not pay rewards for reports. We will credit you by name on the fix if you
want that.

**Please do not** touch other people's accounts or machines, exfiltrate data,
take the service down, or disclose a vulnerability before it is fixed. We will
not pursue reports that stay within those lines.

## Scope

**The software.** It runs with your privileges on your own machine, and what an
agent may touch there is decided by the rules you wrote. Reports about the
enforcement of those rules — a tool call that ran when the policy should have
stopped it, a path reachable outside the declared workspace roots — are the
highest-value ones.

**The hosted service.** Account handling, the relay, pairing, and billing.

Out of scope: findings that require an attacker to already control the machine
the software runs on, and the behaviour of AI models themselves, which we
neither train nor control.

## The full policy

The published version, including how the system is built and what it does not
store, is at <https://contenox.com/legal/security>. Where this file and that
page differ, that page is current.
