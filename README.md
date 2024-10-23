# Exp-13-Implement-Message-Authencation-Code

# AIM:

To generate and verify a Message AuthenƟcaƟon Code (MAC) for ensuring the integrity and
authenƟcity of a message using a simple XOR operaƟon.

# DESIGN STEPS:

Step 1: Input a secret key and a message from the user.

Step 2: Generate the MAC by applying a simple XOR operaƟon between the secret key and the
message.

Step 3: The MAC is computed by repeaƟng the key or message as necessary.

Step 4: The user can input a received MAC, and the program verifies whether the received MAC
matches the computed MAC.

Step 5: The authenƟcity of the message is confirmed if the MACs match.

# PROGRAM:
```
#include <stdio.h>
#include <string.h>

#define MAC_SIZE 32 // Define MAC size in bytes

// FuncƟon to compute a simple MAC using XOR
void computeMAC(const char *key, const char *message, char *mac) {
int key_len = strlen(key);
int msg_len = strlen(message);

// XOR the key and message, repeaƟng if necessary
for (int i = 0; i < MAC_SIZE; i++) {
mac[i] = key[i % key_len] ^ message[i % msg_len]; // Simple XOR operaƟon
}
mac[MAC_SIZE] = '\0'; // Null-terminate the MAC string

}

int main() {
char key[100], message[100];
char mac[MAC_SIZE + 1]; // Buffer for MAC (+1 for null terminator)
char receivedMAC[MAC_SIZE + 1]; // Buffer for input of received MAC

// Step 1: Input secret key
prinƞ("Enter the secret key: ");
scanf("%s", key);

// Step 2: Input the message
prinƞ("Enter the message: ");
scanf("%s", message);

// Step 3: Compute the MAC
computeMAC(key, message, mac);

// Step 4: Display the computed MAC in hexadecimal
prinƞ("Computed MAC (in hex): ");
for (int i = 0; i < MAC_SIZE; i++) {
prinƞ("%02x", (unsigned char)mac[i]); // Print each byte as hex
}
prinƞ("\n");

// Step 5: Input the received MAC (for verificaƟon)
prinƞ("Enter the received MAC (as hex): ");
for (int i = 0; i < MAC_SIZE; i++) {
scanf("%02hhx", &receivedMAC[i]);
}

// Compare the computed MAC with the received MAC
if (memcmp(mac, receivedMAC, MAC_SIZE) == 0) {
prinƞ("MAC verificaƟon successful. Message is authenƟc.\n");
} else {
prinƞ("MAC verificaƟon failed. Message is not authenƟc.\n");
}

return 0;
}
```
# Output:

![image](https://github.com/user-attachments/assets/20741404-83e9-47b4-a3c2-6b9b72c6559f)

# RESULT:

The program for generaƟng and verifying a Message AuthenƟcaƟon Code (MAC) was executed
successfully, demonstraƟng the integrity and authenƟcity of the message through a simple XOR-
based MAC.
