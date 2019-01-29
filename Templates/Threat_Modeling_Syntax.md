## **Threat Modeling Syntax Information**

#### Interaction Syntax
* <-->
    - designates a physical communication connection
* <-(Service Here)->
    - You may add detail as to the service used with parenthesis inside of the connection arrows
    - __Ex:__ User <-(nginx)-> Web App
* Node [Action]
    - Use square brackets to specify specific actions or routes used on a node for that connection
    - __Ex:__ User <--> Rails API [Log in] <--> Credential Database
* Node [Action (Detail)]
    - Use parenthesis inside of the square brackets to provide further detail
    - __Ex:__ Admin User <--> Web App [Admin Console (Manage Project Access)] <--> Database
* Server One/Server Two
    - Use forward slash to list multiple nodes using the same connection route
    - __Ex:__ Demo/Staging/Production Servers <--> GitLab [Project Repo]

#### Diagram Syntax
* Each diagram must contain a key that holds all symbol information
* Colors are optional, but meaningful color differences should be defined by the diagram key
* Solid rectangles with sharp corners
    - Designates object grouping or server boundaries
    - Must be named with a label in a corner
* Solid rectangles with rounded corners
    - Designates an action or service
    - Must be named with a label in the center
* Solid outlined cloud
    - Represents a group of servers
    - Must be named with a label in the center
* Dashed rectangles
    - Used to designate network or authentication boundaries
    - Surrounds actions or objects that require a certain privilege
    - Must be named with a label in the corner
* Closed and filled in arrows
    - Represents the initial direction of data flow in a connection
* Open/hollow arrows
    - Represents the return direction of data flow, in connections that return a response
        * This does not include acknowledgement packets or their equivalent