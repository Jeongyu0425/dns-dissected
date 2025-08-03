# 🧠 DNS Dissected

This is a personal learning log of how **DNS (Domain Name System)** works — written as I explored the concepts behind domain names, IP addresses, queries, and caching.  
It's structured for both beginners and fellow learners trying to understand networking fundamentals.

---

## 📗 Section 1: DNS Basics

- **DNS = Domain Name System**
- It converts human-readable domain names (like `openai.com`) into machine-readable IP addresses.
- It works like a **phonebook**: you search by name and get the address.

> ✍️ *Without DNS, we'd have to memorize `142.250.72.206` instead of `google.com`.*

---

## 🧾 Section 2: DNS Resolution Flow

DNS involves four key servers that work together:

| Server                | Analogy                        | Role |
|-----------------------|--------------------------------|------|
| **DNS Recursor**      | Librarian                      | Receives query, does the lookup |
| **Root Name Server**  | Library index                  | Directs to TLD server |
| **TLD Name Server**   | Bookshelf label (e.g., `.com`) | Directs to authoritative server |
| **Authoritative NS**  | Dictionary                     | Holds the actual IP record |

---

## 🔁 Section 3: Queries & Caching

There are **3 types of DNS queries**:

- **Recursive:** “Find the full answer for me.”
- **Iterative:** “Give me your best guess; I’ll ask the next.”
- **Non-recursive:** Direct lookup, usually from cache.

🧠 *Analogy:*
- **Recursive** = Ask a concierge to find a café and wait for them to return.
- **Iterative** = Walk around and ask people until someone knows.
- **Non-recursive** = Ask someone who already knows the answer.

### ⚡ DNS Caching

- First, the **browser** checks its DNS cache.
- Then, the **OS stub resolver**.
- Finally, **DNS resolvers** on the network.

Caching improves performance by skipping unnecessary queries.

---

## 🏷️ Tags  
`DNS` • `Networking` • `Beginner` • `Technical Notes` • `Self-Taught`

---

## 🙋‍♂️ Why I Wrote This

I’m learning cybersecurity and computer networking from scratch, and this project helped me better understand how the Internet works.
