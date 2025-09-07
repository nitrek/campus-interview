# Question Bank: Computer Networks

This section covers fundamental concepts of computer networking, including protocols, layers, and models.

---

## **Table of Contents**
- [Question Bank: Computer Networks](#question-bank-computer-networks)
  - [**Table of Contents**](#table-of-contents)
  - [**Easy**](#easy)
    - [**Question:** What are the OSI and TCP/IP models? What are their layers?](#question-what-are-the-osi-and-tcpip-models-what-are-their-layers)
    - [**Question:** What is the difference between TCP and UDP?](#question-what-is-the-difference-between-tcp-and-udp)
    - [**Question:** What is a DNS? How does it work?](#question-what-is-a-dns-how-does-it-work)
  - [**Medium**](#medium)
    - [**Question:** Explain the process of a TCP three-way handshake.](#question-explain-the-process-of-a-tcp-three-way-handshake)
    - [**Question:** What is the difference between HTTP and HTTPS?](#question-what-is-the-difference-between-http-and-https)
    - [**Question:** What is a firewall and what does it do?](#question-what-is-a-firewall-and-what-does-it-do)
  - [**Difficult**](#difficult)
    - [**Question:** Explain how NAT (Network Address Translation) works. Why is it used?](#question-explain-how-nat-network-address-translation-works-why-is-it-used)
    - [**Question:** What happens from the moment you type google.com into your browser and press Enter until the page loads?](#question-what-happens-from-the-moment-you-type-googlecom-into-your-browser-and-press-enter-until-the-page-loads)
    - [**Question:** Explain BGP (Border Gateway Protocol). Why is it important?](#question-explain-bgp-border-gateway-protocol-why-is-it-important)

---

## **Easy**

### **Question:** What are the OSI and TCP/IP models? What are their layers?

**Answer:**  
They are conceptual models that standardize the functions of a telecommunication or computing system in terms of abstraction layers.

- **OSI Model (Open Systems Interconnection):** A 7-layer model.
  1. Physical  
  2. Data Link  
  3. Network  
  4. Transport  
  5. Session  
  6. Presentation  
  7. Application  

- **TCP/IP Model:** A 4-layer (or sometimes 5-layer) model that is more practical and widely used.
  1. Network Interface / Link  
  2. Internet (corresponds to OSI Network)  
  3. Transport  
  4. Application (corresponds to OSI Session, Presentation, Application)  

**Hint:**  
Remember the OSI layers with a mnemonic like:  
*"Please Do Not Throw Sausage Pizza Away."*

---

### **Question:** What is the difference between TCP and UDP?

**Answer:**  
- **TCP (Transmission Control Protocol):**  
  - Connection-oriented protocol.  
  - Guarantees ordered, reliable, error-free delivery.  
  - Uses a three-way handshake, performs error checking, and retransmits lost packets.  
  - Used for applications where reliability is critical: **HTTP, SMTP, FTP**.  

- **UDP (User Datagram Protocol):**  
  - Connectionless protocol.  
  - No guarantee of delivery, order, or error checking.  
  - Faster but less reliable.  
  - Used for speed-sensitive apps: **Video streaming, Online gaming, DNS lookups**.  

**Hint:**  
TCP is like a registered letter; you get confirmation it was delivered correctly.  
UDP is like a standard postcard; you send it and hope it gets there, but it's faster.

**Follow-up:**  
Can you describe the TCP three-way handshake?

---

### **Question:** What is a DNS? How does it work?

**Answer:**  
DNS (Domain Name System) is the phonebook of the internet. It translates human-readable domain names (like `www.google.com`) into machine-readable IP addresses (like `172.217.16.142`).

**Process:**  
- Browser sends a query to a DNS resolver (usually your ISP).  
- If not cached, resolver queries:
  - **Root server → TLD server → Authoritative Name Server**  
- IP address is returned to the browser to establish a connection.  

**Hint:**  
Think of it as a translator from names to numbers.

---

## **Medium**

### **Question:** Explain the process of a TCP three-way handshake.

**Answer:**  
The three-way handshake is the process TCP uses to establish a connection between a client and a server.

**Steps:**
1. **SYN:** Client → Server (sends SYN flag to open connection).  
2. **SYN-ACK:** Server → Client (responds with SYN + ACK).  
3. **ACK:** Client → Server (acknowledges and connection established).  

**Hint:**  
Like a phone call:  
- Client: "Hello, are you there?" (**SYN**)  
- Server: "Yes, I’m here and I hear you!" (**SYN-ACK**)  
- Client: "Great, I hear you too!" (**ACK**)  

**Follow-up:**  
How is a TCP connection terminated? (Four-way handshake with FIN flags).

---

### **Question:** What is the difference between HTTP and HTTPS?

**Answer:**  
- **HTTP (HyperText Transfer Protocol):**  
  - Communication between browsers and servers in plain text.  
  - Not secure (susceptible to MITM attacks).  
  - Uses **port 80**.  

- **HTTPS (HyperText Transfer Protocol Secure):**  
  - Encrypts communication using **TLS/SSL**.  
  - Provides **confidentiality, integrity, authentication**.  
  - Uses **port 443**.  

**Hint:**  
The "S" stands for **Secure**, provided by encryption (TLS/SSL).

**Follow-up:**  
Can you briefly explain how the SSL/TLS handshake works?

---

### **Question:** What is a firewall and what does it do?

**Answer:**  
A firewall is a **network security device** that monitors and controls incoming and outgoing traffic based on security rules.  
It acts as a **barrier between a trusted network and an untrusted network** (like the Internet).  
Can be **hardware, software, or both**.  

**Hint:**  
Like a security guard checking IDs (packet info) before allowing entry.

**Follow-up:**  
What’s the difference between a **stateful** and a **stateless** firewall?

---

## **Difficult**

### **Question:** Explain how NAT (Network Address Translation) works. Why is it used?

**Answer:**  
NAT maps multiple private IP addresses to a single public IP before sending data to the Internet.  

**How it works:**  
- Device sends request → Router replaces private IP with its public IP → Maintains mapping in NAT table.  
- Response returns → Router translates back to private IP → Forwards to correct device.  

**Uses:**  
- Conserve IPv4 addresses.  
- Add security by hiding internal network.  

**Hint:**  
Like a receptionist: all mail goes to the building’s main address (public IP), then delivered internally.

**Follow-up:**  
What’s the difference between **static NAT**, **dynamic NAT**, and **PAT (Port Address Translation)**?

---

### **Question:** What happens from the moment you type google.com into your browser and press Enter until the page loads?

**Answer:**  
**Steps:**
1. **DNS Lookup:** Resolve domain name to IP.  
2. **TCP Handshake:** Establish TCP connection (SYN, SYN-ACK, ACK).  
3. **TLS Handshake (for HTTPS):** Negotiate encryption and exchange keys.  
4. **HTTP Request:** Browser sends HTTP GET request.  
5. **Server Processing:** Server processes request, fetches data.  
6. **HTTP Response:** Server sends response (HTML, CSS, JS).  
7. **Browser Rendering:**  
   - Parse HTML → Build DOM.  
   - Load CSS → Build CSSOM.  
   - Combine → Render tree → Paint → Execute JS.  

**Hint:**  
Follow the data path: **DNS → TCP → HTTP → Rendering**.

---

### **Question:** Explain BGP (Border Gateway Protocol). Why is it important?

**Answer:**  
BGP is the **routing protocol of the Internet**, used to exchange routing info among **autonomous systems (AS)**.

- **Type:** Path-vector protocol.  
- **Function:** Makes routing decisions based on paths, policies, and rules—not just shortest path.  
- **Importance:**  
  - Connects major networks globally.  
  - Decides best paths for Internet traffic.  

**Hint:**  
If other routing protocols are like **city street navigation**, BGP is the **highway system connecting cities**.

**Follow-up:**  
What is **BGP hijacking** and why is it a security concern?

---
