# cs6238-project-4-solved



**<span style='color:red'>TO GET THIS SOLUTION VISIT:</span>** https://www.ankitcodinghub.com/product/cs6238-secure-computer-systems-spring-project-4-secure-shared-store-3s-solved/

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;114888&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;0&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;0&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;0\/5 - (0 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CS6238 Project 4 Solved&quot;,&quot;width&quot;:&quot;0&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">
            
<div class="kksr-stars">
    
<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
    
<div class="kksr-stars-active" style="width: 0px;">
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>
                

<div class="kksr-legend" style="font-size: 19.2px;">
            <span class="kksr-muted">Rate this product</span>
    </div>
    </div>
<strong>IMPORTANT NOTE</strong>: We will not accept PyCrypto, Crypto, or Cryptodome libraries in project four. Use the cryptography library <a href="https://cryptography.io/en/latest/">(</a><a href="https://cryptography.io/en/latest/">https://cryptography.io/en/latest/</a><a href="https://cryptography.io/en/latest/">)</a>&nbsp; for this project. We will not give credit for any effort using the prohibited libraries.

&nbsp;

<h1>Goals &amp; Assumptions</h1>
This project is based on the topic of distributed systems security that is covered in Modules 11 and 12. The goal of the project is to gain hands-on experience in implementing secure distributed services. You will develop a simple <em>Secure Shared Store (</em>3S) service that allows for the storage and retrieval of documents created by multiple users who access the documents at their local machines. In the implementation, the system should consist of one or more 3S client nodes and a single server that stores the documents.

Users should be able to login to the 3S server through any client by providing their private key as discussed in Module 12. Session tokens would be generated upon successful authentication of the users. They can then check-in, checkout and delete documents as allowed by access control policies defined by the owner of the document.

To implement such a distributed system, we will need to make use of certificates to secure the communication between clients and the server, and to authenticate sources of requests. You will need to make use of a Certificate Authority (CA) that generates certificates for users, client nodes and the server. All nodes trust the CA.

&nbsp;

<h1>Project Setup</h1>
We have provided a Virtual Machine for the project. <strong>Links to download the image (.ova file) will be posted on Ed Discussion</strong>.

The default account on the VM is <strong>cs6238 </strong>and the password is <strong>cs6238</strong>. The root password is also <strong>cs6238</strong>. In an ideal setting, the 3S server and the client would be on separate nodes. For simplicity, we have set up only one VM. The server and client nodes are abstracted as separate folders within the VM. For example, the <em>server </em>folder represents the server and the <em>client1 </em>folder represents the client node.

The desktop contains a Project4 folder which has the skeletal implementation of the 3S service. You will be required to complete the implementation to satisfy all the functionalities which will be detailed below. The Project4 folder contains:

<ol>
<li><strong>CA </strong>– Represents the Certificate Authority and contains the CA certificates</li>
<li><strong>server </strong>– Represents the server. It contains server certificates and the 3S application code. The 3S server is implemented using Python Flask and <em>py</em> contains the outline of the server code which is to be fully completed.</li>
<li><strong>client1 </strong>– Represents one of the client nodes. <em>py</em> has the skeletal implementation of the client. You will be required to generate client certificates and place them in the client1/certs folder.</li>
<li><strong>client2 </strong>– Represents another client node and the environment should be similar to client1.</li>
</ol>
&nbsp;

Fig: Folder structure of Project4

&nbsp;

<h2>Certificates</h2>
As discussed above, we will need to make use of a Certificate Authority that is trusted by all nodes. This CA would be used to generate certificates for the users, client nodes and the server. One can make use of a library such as <strong>OpenSSL </strong>for setting up the CA and to generate certificates.

For this project, we have created a CA. This CA has been used to generate certificates for the server. You would be required to generate certificates for the client nodes using this CA. The CA (certificate and key) was generated using the password (passphrase) <strong>cs6238</strong>.

Detailed instructions on generating certificates are present in Appendix A.

When the client keys and certificates are created, they should be placed in the clientX/certs folder and should be named as clientX.key and clientX.crt

&nbsp;

<h1>3S Implementation Details</h1>
After a 3S server starts, a client node can make requests to the server. Let’s assume that client nodes have a discovery service that allows them to find the hostname where 3S runs. The hostname, in this case, is <strong>secureshared-store</strong>. The certificate for the server contains <strong>secure-shared-store </strong>as the common name of the server. Whenever the client node makes a request, mutual authentication is performed, and a secure communication channel is established between the client node and the server. Here we make use of nginx to perform mutual authentication (MTLS). Every request from the client node should include the certificate of the client node for authentication.

As mentioned before, the 3S service should enable functions such as login, checkin, checkout, grant, delete, and logout. You will have to complete the skeleton code provided for the server and client to achieve these functionalities. Details are as follows:

<ol>
<li><strong>login(User UID, UserPrivateKey)</strong>: This call allows a client node to generate necessary statements to convince the 3S server that requests made by the client are for the user having UID as its user-id. The client node will take UID and UserPrivate key as two separate inputs from the user. The filename of the key is to be provided as input as opposed to the key value itself. A user’s private key should only be used to sign the necessary statement, but never sent to the server. The statement should be of the form “<strong><em>ClientX as UserY logs into the Server</em></strong>” where X represents the client-id and Y represents the userid. On successful login, the server should return a unique session-token for the user. The session token will have to be included in all the subsequent requests and would play the role of the statement in those requests. Also, you must ensure that each user has a unique UID. You can assume that a given client node only handles requests of a single user in one session (if a user logs in successfully from another client, the previous session will be invalidated). Example of a public / private key creation with OpenSSL: <a href="https://www.digicert.com/kb/ssl-support/openssl-quick-reference-guide.htm">https://www.digicert.com/kb/ssl</a><a href="https://www.digicert.com/kb/ssl-support/openssl-quick-reference-guide.htm">–</a><a href="https://www.digicert.com/kb/ssl-support/openssl-quick-reference-guide.htm">support/openssl</a><a href="https://www.digicert.com/kb/ssl-support/openssl-quick-reference-guide.htm">–</a><a href="https://www.digicert.com/kb/ssl-support/openssl-quick-reference-guide.htm">quick</a><a href="https://www.digicert.com/kb/ssl-support/openssl-quick-reference-guide.htm">–</a><a href="https://www.digicert.com/kb/ssl-support/openssl-quick-reference-guide.htm">reference</a><a href="https://www.digicert.com/kb/ssl-support/openssl-quick-reference-guide.htm">–</a><a href="https://www.digicert.com/kb/ssl-support/openssl-quick-reference-guide.htm">htm</a><a href="https://www.digicert.com/kb/ssl-support/openssl-quick-reference-guide.htm">.</a></li>
</ol>
&nbsp;

<ol start="2">
<li><strong>checkin(Document DID, SecurityFlag)</strong>: A document with its id (DID = filename) is sent to the server over the secure channel that was established when the session was initiated. If the document already exists on the server, it may be overwritten along with its meta-data. If a new document is checked in, the user at the client node becomes the owner of the document. The owner does not change if the document is updated (using checkin) by an authorized user who is not the owner. The <em>SecurityFlag </em>specifies how document data should be stored on the server. The documents that are to be checked into the server must be present in the documents/checkin folder within the client directory [It is already created within client1]. On the server, the documents that are checked in must be stored in the documents folder within the server directory.</li>
</ol>
When the Security Flag is set as <em>Confidentiality </em>(to be represented by “1”), the server generates a random AES key for the document, uses it for encryption and stores data in the encrypted form. To decrypt the data at a later time, this key is also encrypted using the server’s public key and stored with document meta-data. When the

Security Flag is set as <em>Integrity </em>(to be represented by “2”), the server stores the document along with a signed copy.

&nbsp;

<ol start="3">
<li><strong>checkout(Document DID)</strong>: After a session is established, a user can use this function to request a specific document based on the document identifier (DID) over the secure channel to the server.
<ul>
<li>The request is granted only if the checkout request is made either by the owner of the document or if performed by a user who is authorized to perform this action.</li>
<li>If successful, a copy of the document is sent to the client node.</li>
<li>The server would have maintained information about documents (e.g., meta-data) during checkin that allows it to locate the requested document, decrypt it and send the document back to the requestor.</li>
<li>Once the document is checked out, it must be stored in the documents/checkout folder within the Client directory.</li>
</ul>
</li>
</ol>
When a request is made for a document stored with <em>Confidentiality</em> as the <em>SecurityFlag</em>, the server locates the encrypted document and its key, decrypts the data and sends it back over the secure channel. Similarly, when a request is made for a document stored with <em>Integrity</em> as the <em>SecurityFlag</em>, the signature of the document must be verified before sending a copy to the client.

Additionally, when a request is made to <strong>checkin</strong> a document that is checked out in the current active session, the client must <strong><u>move</u></strong> (not copy) the document from the “/documents/checkout” folder into the

“/documents/checkin” folder. The client implementation must handle the transfer of these files between the folders automatically.&nbsp; t

<ol start="4">
<li><strong>grant(Document DID, TargetUser TUID, AccessRight R, time T)</strong>:
<ul>
<li>Grant can only be issued by the owner of the document.</li>
<li>This will change the defined access control policy to allow the target user (TUID) to have authorization for the specified action (R) for the specified document (DID).</li>
<li>AccessRight R can either be:</li>
</ul>
</li>
</ol>
<strong>i </strong>&nbsp;checkin (which must be represented by input 1)&nbsp; <strong>ii </strong>checkout (which must be represented by input 2)&nbsp;&nbsp; <strong>iii </strong>both (which must be represented by input 3)

for time duration T (in seconds). If the TargetUser is ALL (<strong>TUID=0</strong>), the authorization is granted to all the users in the system for this specific document. If there are multiple grants that have been authorized for a particular document and user, the latest grant would be the effective rule. Basically, <strong>the latest grant for the tuple (DID, TUID) should persist</strong>.

Here are a few clarification scenarios for Grant:

− If an initial grant for (file1, user1, 2, 100) is successful and then a successful grant request (file1, 0, 1, 50) is made, then <strong>file1 </strong>should be accessible for <strong>checkin</strong> <strong>only </strong>to <strong>all users </strong>for <strong>50 seconds</strong>. User1 loses the checkout access given earlier.

− Grant (file1, 0, 3, 100) exists and then a successful grant request (file1, user2, 2, 50), then <strong>file1 </strong>is accessible to <strong>user2 </strong>for <strong>checkout </strong>for <strong>50 seconds </strong>and invalidates the previous grant.

&nbsp;

<ol start="5">
<li><strong>delete(Document DID)</strong>: If the user currently logged in at the requesting client is the document owner, the file is safely deleted. No one in the future should be able to access data contained in it even if the server gets compromised. The deletion of a confidential document should result in permanent removal of the key used to encrypt it.</li>
</ol>
&nbsp;

<ol start="6">
<li><strong>logout()</strong>: Terminates the current session. If any documents received from the server were modified, their new copies must be sent to the server before session termination completes. While checking back in the modified documents, you must set <em>Integrity</em> as the <em>SecurityFlag</em>.</li>
</ol>
&nbsp;

Since this is a security class, you should use secure coding practices. You are also expected to use static code analysis tools such as Pylint, Pyflakes, etc. and minimize the use of unsafe function calls (justify any such calls you need to make by providing inline comments). The report should list tools used to ensure that your code does not have any vulnerabilities. The report should also discuss the threat model and what threats are handled by your implementation.

&nbsp;

Fig. Project Flow

<strong>&nbsp;</strong>

<h1>Project Deliverables</h1>
<ol>
<li>It should cover the following aspects (Each answer need not be more than a few sentences):
<ul>
<li>Architectural design details:</li>
</ul>
</li>
</ol>
−&nbsp; How mutual authentication is achieved in the current implementation of 3S.

−&nbsp; Details on the cryptographic libraries and functions used to handle secure file storage.

−&nbsp; How the user information and metadata related to documents were stored.

<ul>
<li>Implementation details:</li>
</ul>
−&nbsp; Details of how the required functionalities were implemented

−&nbsp; List any features that were not implemented or tested (partial points may be awarded).

−&nbsp; List the assumptions made, if any.

<ul>
<li>Results of the static code analysis and the tools used.</li>
<li>Threat Modelling and the threats currently handled by your implementation.</li>
<li>Your report should be named as <strong>pdf</strong></li>
</ul>
<ol start="2">
<li>Server code
<ul>
<li>This will be the completed version of server.py that was provided.</li>
<li>This must be named as <strong>py </strong></li>
</ul>
</li>
<li>Client node
<ul>
<li>This will be the completed version of client.py that was provided.</li>
<li>This must be named as <strong>py </strong></li>
</ul>
</li>
<li>Requirements
<ul>
<li>This should include all python modules used in your implementation.</li>
<li>You will use the command “pip3 freeze &gt; requirements.txt” to generate the file It should be named as <strong>txt. </strong>This will be used by the auto grader to replicate your environment, so ensure that the command would install the required dependencies.</li>
</ul>
</li>
</ol>
&nbsp;

<strong>Please ensure that you do not zip the files in your submission. Also, please stick to the specified naming conventions since an auto grader would be evaluating your submissions.&nbsp; </strong>

<strong>IMPORTANT: Please ensure that you submit only these 4 files along with the video (See Video Requirements below) that are mentioned and follow the specified naming conventions. Any error in adhering to these guidelines would result in an error with the autograder and would result in a significant loss of points. </strong>

<strong>&nbsp;</strong>

<strong>&nbsp;</strong>

<h1>Additional Instructions</h1>
<ul>
<li>Please go through the comments in <em>py</em> and <em>client.py</em> and follow the provided instructions. Ensure to complete the sections where TODOs are specified. You can add utility functions as required.</li>
<li>All requests sent from the client must make use of the post_request() utility function and do not modify this function. A sample response format is given in the login() function within the server code. Feel free to make use of the same for the other server function.</li>
<li>Expected response status codes for different scenarios are provided in the server.py for each function. Ensure that the completed code behaves accordingly since the auto grader would use the status for verification. (Status codes provided are custom status codes and not the standard ones. Using custom status codes in HTTP is not best practice, however, this is being used for the purpose of the auto grader) Failure to follow the provided instructions would result in unnecessary point loss.</li>
<li>Run the script <strong>sh</strong> present in the server directory to start the server. It essentially invokes server.py to start the server.</li>
<li>Make sure that the status of nginx is active by using the command – <strong>systemctl status nginx</strong>. If the status is not active, you can restart it using the command – <strong>sudo systemctl restart nginx</strong></li>
<li>Ensure that your implementation can be run and tested by just invoking the <strong>sh</strong> and <em>client.py</em>. Your code must also automatically initialize the required databases, if any and this is necessary so that the autograder can successfully be run. Additionally, ensure that your code would create any folders as necessary by your implementation since we would be using just the two python scripts for evaluation.</li>
<li>No specific test cases will be provided for this project, and you are free to develop a test harness that consists of a sequence of calls made to the 3S server. However, we will soon be releasing a basic testing script to give you an idea of how inputs are provided to the client.</li>
<li>Make sure to test your 3S implementation using at least 2 clients and 3 users. <strong>The autograder would be tested with users named ‘user1’, ‘user2’, ‘user3’ </strong><strong>[these are the UIDs] and clients named ‘client1’, ‘client2’. Please make sure your implementation would be able to support these. The auto grader would also expect userX.key and userX.pub as the private and public keys for those users. So, ensure to test with these three users and create any metadata (in your application and database) as required to support this mapping with the necessary files, keys or paths. </strong></li>
</ul>
<strong><u>IMPORTANT:</u> Do not hardcode the public or private key names (eg: user1.key or user1.pub) in your code. Make sure the usernames and keys are all in lowercase only. </strong>

<ul>
<li>When the client keys and certificates are created, they should be placed in the clientX/certs folder and should be named as clientX.key and clientX.crt <strong>(this is an important setup step.).</strong> These must be used in client.py when the post_request() is invoked.</li>
<li>While sending requests some of you might encounter SSL errors and to avoid this issue, please have a look at the python package <strong>certifi</strong> for this. (You can use this link as a reference – <a href="https://incognitjoe.github.io/adding-certs-to-requests.html">https://incognitjoe.github.io/addi</a><a href="https://incognitjoe.github.io/adding-certs-to-requests.html">n</a><a href="https://incognitjoe.github.io/adding-certs-to-requests.html">g</a><a href="https://incognitjoe.github.io/adding-certs-to-requests.html">–</a><a href="https://incognitjoe.github.io/adding-certs-to-requests.html">cer</a><a href="https://incognitjoe.github.io/adding-certs-to-requests.html">t</a><a href="https://incognitjoe.github.io/adding-certs-to-requests.html">s</a><a href="https://incognitjoe.github.io/adding-certs-to-requests.html">–</a><a href="https://incognitjoe.github.io/adding-certs-to-requests.html">t</a><a href="https://incognitjoe.github.io/adding-certs-to-requests.html">o</a><a href="https://incognitjoe.github.io/adding-certs-to-requests.html">–</a><a href="https://incognitjoe.github.io/adding-certs-to-requests.html">h</a><a href="https://incognitjoe.github.io/adding-certs-to-requests.html">t</a><a href="https://incognitjoe.github.io/adding-certs-to-requests.html">m</a><a href="https://incognitjoe.github.io/adding-certs-to-requests.html">l</a><a href="https://incognitjoe.github.io/adding-certs-to-requests.html">)</a></li>
<li>We encourage you all to discuss the project at a high-level on Ed Discussion. Please ensure that you are not over-sharing and&nbsp; maintain&nbsp; academic</li>
</ul>
Halfway through the project, if there are many common doubts, we will consolidate the clarification posts and share it as a note.

<strong>&nbsp;</strong>

<h1>Grading Outline</h1>
<strong>Report – 30 points&nbsp; </strong>

<ul>
<li>Architectural design details – 5 points</li>
<li>Implementation details – 15 points</li>
<li>Security Analysis of the implemented secure shared store – 5 points ● Threat Modelling – 5 points</li>
</ul>
<strong>Implementation of 3S – 70 points </strong>

Each function in the implementation will be scored as below:

<ol>
<li>Login – 10 points
<ul>
<li>Handling the private key of the user and verifying the signature of the created statements</li>
<li>Generation of a session token used for further requests</li>
</ul>
</li>
<li>Checkin – 15 points
<ul>
<li>Secure file transfer of documents</li>
<li>Handling the security flag – Integrity and Confidentiality</li>
<li>Ownership/ Authorization check</li>
</ul>
</li>
<li>Checkout – 15 points
<ul>
<li>Secure file transfer of documents</li>
<li>Handling the security flag – Integrity and Confidentiality</li>
<li>Ownership/ Authorization check</li>
</ul>
</li>
<li>Grant – 15 points
<ul>
<li>Granting authorization to other users</li>
<li>Handling expiry of granted access (in seconds)</li>
</ul>
</li>
<li>Delete – 10 points
<ul>
<li>Ensuring deletion of files</li>
<li>Ownership/ Authorization check</li>
</ul>
</li>
<li>Logout – 5 points
<ul>
<li>Checking in all the modified checked out files and session termination</li>
</ul>
</li>
</ol>
&nbsp;

&nbsp;

<strong>&nbsp;</strong>

<h1>Video Requirements</h1>
As mentioned earlier, this project will be graded by an autograder so please follow the guidelines mentioned in this file. However, there is an alternate solution in the event that the autograder fails for your submission due to any reason. This video (a screen recording) will be <strong>required</strong> to be submitted as part of your submission and will be then graded for partial credit (only if the autograder fails). This must be added as a media comment on your submission and can be of any common video format<strong>.&nbsp; If you fail to submit the video, you’ll take a penalty of 10 points. </strong>

The following steps will be required to be shown as a part of your video:

<ul>
<li>Download your latest submission from Canvas</li>
<li>Walk through the 6 functions that are mentioned as a part of the Implementation requirements Follow these steps when recording the video:
<ol>
<li>Login as user1 with user1.key</li>
<li>Login as user2 with user2.key</li>
<li>Login as user3 with user1.key</li>
<li>user1 checkin file1 with Security Flag</li>
<li>user2 checkin file2 with Integrity Flag</li>
<li>user1 checkout file1</li>
<li>user2 checkout file2</li>
<li>user1 checkout file2</li>
<li>user2 checkout file1</li>
<li>user1 grant checkout file1 to user2</li>
<li>user2 checkout file 1 (within the granted time for step 10)</li>
<li>user3 checkout file 1 (within the granted time for step 10)</li>
<li>Wait for the granted period in step 10 to expire and try 11 again</li>
<li>user1 delete file 1</li>
<li>user1 delete file 2</li>
<li>user2 delete file 2</li>
<li>Logout</li>
</ol>
</li>
</ul>
The video should show the file locations and content. Try to show as many details about the functionality of the program as possible.

<ul>
<li>The entire duration of this <strong>video should not exceed 10 minutes</strong>, but we are flexible.</li>
</ul>
&nbsp;

<strong>&nbsp;</strong>

<h1>APPENDIX A</h1>
<strong>Certificate Generation</strong>:

The resource below describes how to set up a Certificate Authority (CA) and then how it’s certificate would be used to generate certificates for the nodes.

<ul>
<li>&nbsp; <a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">https://deliciousbrains.com/s</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">s</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">l</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">–</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">certifica</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">t</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">e</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">–</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">authori</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">t</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">y</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">–</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">f</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">o</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">r</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">–</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">loc</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">al</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">–</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">htt</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">p</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">s</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">–</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">developmen</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">t</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">/</a><a href="https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/">&nbsp;&nbsp; </a></li>
</ul>
We have already set up a CA. You can find the CA certificates in the CA folder of Project4. We have also generated the server keys and certificate (certname is <strong>secure-shared-store</strong>) using the CA certificate. Also, the following command was used to extract the public key from the certificate.&nbsp; <strong>openssl x509 -pubkey -noout -in</strong><strong> secure-shared-store.crt &gt; secure-shared-store.pub</strong> You can use the above resources to generate certificates and keys for the client nodes and users.

&nbsp;
