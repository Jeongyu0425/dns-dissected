# dns-dissected
A personal walkthrough of DNS basics — how domain names translate to IP addresses, how DNS servers work together, and how queries and caching speed things up. Written in my own words with analogies for easier understanding.


## **Section 1: DNS Basics & Purpose**

**DNS** helps humans when entering a domain name by converting it into an **IP address**, which is more machine-friendly. It means we don’t have to memorize long or complex IP addresses every time we want to visit a website. We just type the **domain name**, and DNS handles the rest.

**DNS** stands for **Domain Name System**. Its basic function is to let users use **domain names** instead of memorizing **IP addresses**. Without it, we’d have to deal with numeric strings, which isn’t realistic for most people.

The **domain name** is easier for humans to understand and remember, and the **IP address** is what computers use to find each other. **DNS** connects those two so the user and the machine can communicate properly.

It’s compared to a **phonebook** because it helps find the exact address (**IP**) of a website based on its name. Just like how you’d look up someone’s phone number by their name, **DNS** lets your browser look up the **IP address** of a **domain name** so the site can load.


## **Section 2: DNS Server Types & Resolution Process**

There are four main **DNS servers** involved in a query: the **DNS Recursor**, the **Root Name Server**, the **TLD Name Server**, and the **Authoritative Name Server**. These servers work together to get the correct **IP address** for a **domain name**.

The **DNS Recursor** is like a librarian. When you give it a **domain name**, it tries to find the **IP address** for you by reaching out to other **DNS servers**. It’s the one that takes the initial request and starts the lookup process.

The **Root Name Server** is the first stop. It’s like a label telling the recursor which section of the library to check. It doesn’t have the full answer but points to the right direction.

The **TLD Name Server** helps narrow it down further. It’s like going to the right shelf in the library. It gives the **DNS Recursor** the next step in the search.

The **Authoritative Name Server** is the final stop. It’s like the dictionary that gives the exact **IP address** for the **domain** you’re trying to reach. Once the **DNS Recursor** gets this info, it returns it to the client so the browser can load the site.


## **Section 3: DNS Queries and Caching**

Clients send **queries** to **DNS servers** to get the **IP address** that matches a **domain name**. There are three types of queries: **non-recursive**, **recursive**, and **iterative**.

A **recursive query** is when the client asks a **DNS resolver** to go find the answer completely and come back with either the result or an error. The client doesn’t do anything — it only waits for the full answer.

An **iterative query** is a process where the client asks one **DNS server** for the best answer it can give. If the server doesn’t have the record, it sends back a **referral** — basically pointing to another server that might have it. The client then continues asking based on those referrals until it either finds the **IP address** or times out.

In that **iterative process**, each time the client sends a request and waits for either a record or a referral, it’s performing a **non-recursive query**. These are the small, direct “Do you know the answer?” requests that make up the **iterative chain**.

To make it easier to understand, I came up with this analogy:  
A **recursive query** is like a customer asking a hotel concierge where the Matcha café is. The concierge (acting like the **DNS resolver**) goes out and asks others until he either finds it or gives up. Meanwhile, the customer just waits in the lobby.  
An **iterative query** is more like walking down the street and asking people for directions. Each person might say, “I don’t know, but try asking that person over there.” You keep going until someone gives you the actual location — or no one does.  
Each time you ask someone in that process — just asking if they know — that’s a **non-recursive query**.

**Caching** also plays a big role in speeding things up. **DNS caching** is like a memory shortcut. Instead of going through the whole lookup process every time, the system checks to see if it already knows the answer. First, the **browser** checks its own **DNS cache**. If it’s not there, it checks the **operating system’s cache**. If it’s still not found, then it asks the **DNS servers**. This helps avoid unnecessary steps and makes the whole process faster.

---
