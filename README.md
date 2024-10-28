# Project idea: virtual gallery for 3D objects
members: Csutak Lilla, Paliciuc Alex

# 3 Layered Structure:
1. Presentation Layer:    
  Technologies    
    -> Web Framework:    
    -> 3D Rendering:    
    -> Styling:    
  Responsabilities    
    -> rendering 3D artwork    
    -> fetching & submitting data by API calls to backend     
    -> handle real-time updates (uploading etc.)     
    -> handle views (gallery view, artwork view, profile settings etc.)    
2. Business Logic Layer:    
   Technologies     
     -> Server framework: node.js with express   
     -> WebSockets: Socket.io    
     -> Authentication:    
   Responsabilities:    
     -> Business logic modules for handling specific functionalities (user management, artwork management, gallery managament, real-time events)    
     -> API endpoints    
     -> Authentification & Authorization    
     -> connection between Presentation Layer and DB Layer      
3. Database Layer     
   Technologies:     
     -> DB: MongoDB     
   Responsabilities:       
     -> Data Models: Mongoose      
     -> Data Access Layer: CRUD     
