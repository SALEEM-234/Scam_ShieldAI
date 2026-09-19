# 🛡️ ScamShield AI

### Know who's calling. Understand what they're saying.

ScamShield AI is a real-time AI-powered scam call detection system designed to help protect elderly users from evolving phone scams.

Instead of depending only on caller ID or previously reported scam numbers, ScamShield combines **Caller Intelligence** with **Conversation Intelligence** to understand both who is calling and what is being said during the conversation.

---

## 🚨 Problem

Scammers increasingly use fresh or spoofed phone numbers, making traditional caller-ID and reported-number-based detection insufficient.

Common scams include:

- Fake KYC verification calls
- Bank impersonation
- OTP and credential requests
- UPI/payment scams
- Fake customer-support calls
- "Family member in trouble" scams
- Threat-based and urgency-driven manipulation

The key challenge is detecting a scam **during the conversation**, before the user shares sensitive information or makes a payment.

---

## 💡 Our Solution

ScamShield AI analyzes both caller-related signals and the content of the conversation.

### Two-Layer Intelligence

**1. Caller Intelligence**

Analyzes available caller information and spam indicators.

**2. Conversation Intelligence**

Uses Speech-to-Text and an LLM-based analysis layer to understand:

- Scam intent
- Urgency
- Threats and fear
- Authority impersonation
- OTP/credential requests
- Payment requests
- Secrecy and isolation tactics
- Overall conversational context

These signals are combined by a **Risk Engine** to generate a simple risk level:

🟢 Low Risk  
🟡 Medium Risk  
🔴 High Risk

---

## 🧠 AI Approach

ScamShield is designed to go beyond simple keyword matching.

A scammer can change the wording of a known scam script while keeping the same underlying manipulation strategy.

For example:

> "Your account will be suspended today. Read the verification code immediately."

and

> "There is a security issue with your account. Give me the code you just received before access is restricted."

Although the wording differs, the underlying signals may include:

- Urgency
- Authority/security claim
- Account threat
- Verification-code request

The LLM analyzes the **meaning and context** of the conversation rather than relying only on exact phrases.

---

## 🎯 Primary Objective

### Detect novel scam scripts and reduce false negatives

The system is designed to identify scam patterns even when the scammer uses previously unseen wording.

### Secondary Objectives

- Reduce false positives
- Provide alerts with low latency
- Explain why a conversation is considered risky
- Protect user privacy

---

## 🛡️ False-Positive Mitigation

Urgency alone does not mean a call is a scam.

For example, a hospital call may contain urgent language without requesting an OTP, payment, password, or other sensitive information.

ScamShield therefore considers **multiple contextual signals together** rather than triggering a high-risk alert from a single keyword or phrase.

Example:

**Genuine urgent call**

Urgency + legitimate context + no sensitive-information request  
→ Lower risk

**Potential scam**

Urgency + impersonation + threat + OTP/payment request  
→ Higher risk

---

## 🏗️ System Architecture

```text
                 📞 Incoming Call
                        |
              +---------+---------+
              |                   |
              v                   v
     Caller Intelligence   Conversation Audio
                                  |
                                  v
                         Speech-to-Text
                                  |
                                  v
                         LLM Analysis
                                  |
                                  v
                    Manipulation Signals
                                  |
              +-------------------+-------------------+
              |                                       |
              v                                       v
      Caller Risk Signals                    Conversation Risk
              |                                       |
              +-------------------+-------------------+
                                  |
                                  v
                            Risk Engine
                                  |
                    +-------------+-------------+
                    |             |             |
                    v             v             v
                 🟢 LOW       🟡 MEDIUM      🔴 HIGH
                                  |
                                  v
                           User Warning
                                  |
                                  v
                     Optional Family Alert
