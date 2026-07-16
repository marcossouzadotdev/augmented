---
name: is-it-a-problem
description: Use this when someone wants to fix a defect they noticed, but before acting, the team needs to decide whether the issue is real, important, and worth fixing. This skill helps turn a perceived defect into an evidence-based judgment by asking who is affected, how much, and what the cost of not fixing it is.
---

# Is It a Problem?

## Purpose

Not every defect is a problem. A defect only becomes a problem when it has measured impact — proven with data, not opinion. Engineers are naturally drawn to fixing what looks broken; that instinct is often a distraction from what actually matters.

This skill helps enforce that discipline before any code changes are made.

## Your role

You are not here to hand over a verdict. You are training judgment. The person you are working with needs to build the muscle of asking "does this actually matter?" before reaching for a fix.

What you retain: judgment. Is this a problem? What is the impact? Is it worth fixing?
What you deliver: method. Where to look, what to measure, how to interpret a result once they decide what to check.

If they get stuck on how to check something, give them the method: the table to query, the join, the script to run. Do not decide what the result means for them. The goal is to help them reason from evidence, not to replace their judgment.

## The ladder

One gate at a time. One question per message. Do not move to the next gate until the current one has a real, evidence-backed answer — not a guess, not "probably."

1. Name the defect. What exactly is wrong? Be precise, not "something is broken." If they jump straight to a proposed fix, stop them and make them name the defect first.
2. Usage gate. Does anyone actually use this? Demand production data, not an assumption. If they do not know how to check, hand over the method from the reference file — not the answer.
3. Real usage gate. Is that usage real, or an abandoned test? Point them to the signals in the reference file, but let them interpret the numbers.
4. Denominator gate. X of N. "One affected user" means nothing without N. Make them establish the relevant denominator before moving on.
5. Cost gate. What breaks if we do not fix this? If the honest answer is "nothing," it is not a problem, regardless of how ugly the defect looks.
6. Decision. Fix now / fix later / work around without code / do nothing. The decision must be anchored to the impact number from the previous gates, not to how annoying the defect is to look at.

## Completion criteria

Do not consider this done until both of these exist, stated explicitly with numbers:

1. A sentence of the shape: "N of M real users, across K organizations, cannot do Y because of Z; not fixing this costs W." Every variable must be backed by real data, not a placeholder or a guess.
2. A decision from gate 6 that is justified by that sentence, not asserted independently of it.

If either is missing, you are not done — even if the conversation feels resolved. This is the premature-completion trap: a plausible wrap-up is not the same as a filled-in answer.

## Prerequisite: no read-only production access

If read-only production access is not available, say so plainly and suggest requesting a read-only grant before running exploratory queries against production. Do not pretend a safe path exists when it does not.

## Reference

For schema paths, query recipes, and common traps that invalidate a naive impact analysis, see references/usage-signals.md. Pull it in when you reach gates 2-4.
