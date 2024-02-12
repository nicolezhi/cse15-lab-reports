# **Week 2 Lab Report**
***
## Part 1: ChatServer

**code for `ChatServer`**
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // array list to store strings
    String output = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return output;
        } 
        else {
            if (url.getPath().contains("/add-message")) {

                // split url before and after '&' sign into array
                // [s=Hello, user=jpolitz]
                String[] parameters = url.getQuery().split("&");

                // split key & value by '=' sign 
                // [s, Hello]
                String[] message1 =  parameters[0].split("=");

                // split key & value by '=' sign 
                // [user, jpolitz]
                String[] message2 =  parameters[1].split("=");

                // create temporary string to store values
                String temp = "";

                // store jpolitz in temp string
                if (message2[0].equals("user")) {
                temp += message2[1];
                }

                // store Hello in temp string
                if (message1[0].equals("s")) {
                    temp += ": " + message1[1];
                }

                // store temp string in output string, with new line
                output += temp + "\n";
                return output;
            }
            return "404 Not Found!";
        }
    }
}

class ChatServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
**Screenshot of `/add-message?s=Hello&user=jpolitz`**

[Screenshot](https://drive.google.com/file/d/10HAJhlUbCp0uPrWpXvHQ6Yd38rQQsoNc/view?usp=drive_link)

The first method called is handleRequest() which checks if the given URL contains `/` and returns the String output. To get the output: `user: jpolitz`, the code has to split the URL after `/add-message?` into a `parameters` array by the `&` symbol into `[s=Hello, user=jpolitz]`, using the method: `url.getQuery().split("&")`. Then, the code splits the array elements by the `=` sign into `[user, politz]`, using the method: `parameters[1].split("=")`. The code stores `"jpolitz"` gets added to a temporary string called `temp`. Using a similar method: `parameters[0].split("=")` splits the `parameters` array's first element into `[s, Hello]`. `"Hello"` gets stored into the temporary String array, and finally we return the `temp` string to get `"jpolitz: Hello"`. The value of the string `temp` gets changed from empty to storing the name of the user and the message.

**Screenshot of `/add-message?s=How%20are%20you&user=yash`**

[Screenshot](https://drive.google.com/file/d/1-oieLs9yix5wNPKcMtXoYPY3jJz9vfbb/view?usp=drive_link)

The code works pretty much the same for this input as it did above, using the same logic on a different input. First, the `url.getQuery().split("&")` method splits the URL into a `parameters` array into 2 elements: `[s=How are you, user=yash]`. Then, the `parameters[1].split("=")` splits the index: 1 element into `[user, yash]` and stores `"yash"` into a temporary string called `temp`. Then, the `parameters[0].split("=")` method splits the index: 0 element into `[s, How are you]` which stores `"How are you"` into `temp`. Finally, the temporary string gets returned with a new line (`"\n"`) so the output is `"yash: How are you"`in a new line underneath the message printed in the URL above. The difference between this URL and the one above is the values of `String[] message`, `String[] user`, and the `temp` string, since the URL's are different.

***
## **Part 2**

[Screenshot](https://drive.google.com/file/d/17rKX_apciwZ4LSS22VM_Me_C7JlGV3qh/view?usp=drive_link)

The screenshot above shows both the private and public keys when I use the `ls` command. The private key is `id_rsa` and the public key is `id_rsa.pub`. 

[Screenshot](https://drive.google.com/file/d/1PWUxqZ9T9LJDSL3dlHvC39_WbSKGQW4t/view?usp=drive_link)

The screenshot above shows that once I used the `scp` command to log into my account, the next time I logged into my account using `ssh`, it did not prompt me for a password in order to log in.
***

## **Part 3**
This week in lab, I learned how to create my own server and open it on my browser by using `https://localhost`. I thought this was really cool because I had always wondered how code translates into an online server, and it was interesting to get to make my own!
