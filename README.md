# Project idea: virtual gallery for 3D objects
members: Csutak Lilla, Paliciuc Alex

## 3 Layered Structure:
### 1. Presentation Layer:    
  * Technologies    
    &nbsp;&nbsp;&nbsp;&nbsp;-> Web Framework:    
    &nbsp;&nbsp;&nbsp;&nbsp;-> 3D Rendering:    
    &nbsp;&nbsp;&nbsp;&nbsp;-> Styling:    
  * Responsabilities    
    &nbsp;&nbsp;&nbsp;&nbsp;-> rendering 3D artwork    
    &nbsp;&nbsp;&nbsp;&nbsp;-> fetching & submitting data by API calls to backend     
    &nbsp;&nbsp;&nbsp;&nbsp;-> handle real-time updates (uploading etc.)     
    &nbsp;&nbsp;&nbsp;&nbsp;-> handle views (gallery view, artwork view, profile settings etc.)    
### 2. Business Logic Layer:
* Technologies     
     &nbsp;&nbsp;&nbsp;&nbsp;-> Server framework: node.js with express   
     &nbsp;&nbsp;&nbsp;&nbsp;-> WebSockets: Socket.io    
     &nbsp;&nbsp;&nbsp;&nbsp;-> Authentication:    
* Responsabilities:    
     &nbsp;&nbsp;&nbsp;&nbsp;-> Business logic modules for handling specific functionalities (user management, artwork management, gallery managament, real-time events)    
     &nbsp;&nbsp;&nbsp;&nbsp;-> API endpoints    
     &nbsp;&nbsp;&nbsp;&nbsp;-> Authentification & Authorization    
     &nbsp;&nbsp;&nbsp;&nbsp;-> connection between Presentation Layer and DB Layer      
### 3. Database Layer           
* Technologies:     
     &nbsp;&nbsp;&nbsp;&nbsp;-> DB: MongoDB     
* Responsabilities:       
     &nbsp;&nbsp;&nbsp;&nbsp;-> Data Models: Mongoose      
     &nbsp;&nbsp;&nbsp;&nbsp;-> Data Access Layer: CRUD     
***
## Database Structure & API Endpoints
### Tables & Fields
1. ***Artist Table:*** stores infomation about the artist    
&nbsp;&nbsp;&nbsp;&nbsp;Fields:       
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- artist_id (Primary Key)<br> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- name <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- bio <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- profile_pic <br>
2. ***Artworks Table:*** details about each artwork, linking each artwork to one single artist<br>
&nbsp;&nbsp;&nbsp;&nbsp;Fields:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- artwork_id (Primary Key)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- artist_id (Foreign Key)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- title<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- description<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- media_type<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- dimensions (width, height, depth)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- file_id (reference of 3D file stored in GridFS)<br>
3. ***Grid Table:*** fixed grid structure in gallery room, specifying where each artwork will be placed<br>
&nbsp;&nbsp;&nbsp;&nbsp;Fields:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- grid_id <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- x_coordinate<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- y_coordinate<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- z_coordinate<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- artwork_id (reference to artwork)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- is_occupied (boolean)<br>
4. ***GridFS:*** storing artwork files in DB (like 3D objects)<br>
&nbsp;&nbsp;&nbsp;&nbsp;Fields:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- file_id <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- filename <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- size <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- metadata (custom metadata like artwork_id) <br>
### Endpoints
1. *Artists*<br>
* **GET /artist:** retrieves list of artists
* **GET /artists/{id}:** retrieves details for specific artist
* **POST /artists:** adds new artist
* **PUT /artists/{id}:** updates an artist's details
* **DELETE /artists/{id}:** delete artist
2. *Artworks*<br>
* **GET /artworks:** retrieves list of all artworks by artist
* **GET /artwork/{id}:** retrieves details for specific artwork
* **POST /artworks:** adds new artwork & places it in the gallery<br>
&nbsp;&nbsp;&nbsp;&nbsp;(file_id is generated in GridFS;<br> &nbsp;&nbsp;&nbsp;&nbsp;file_id is set in Artworks table;<br>&nbsp;&nbsp;&nbsp;&nbsp;artwork is assigned to next available grid slot in Grid table –> is_occupied is updated and artwork_id fields are set)
* **PUT /artists/{id}:** updates artwork details
* **DELETE /artists/{id}:** delete artist
3. *Grid Management (static)*
* **GET /grid:** retrieves all grid slots with occupancy status
* **GET /grid/{id}:** retrieves details for specific grid-slot
* **POST /artists:** adds new grid-slot to layout
* **PUT /artists/{id}:** updates status of grid slot
