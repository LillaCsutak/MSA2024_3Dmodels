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
