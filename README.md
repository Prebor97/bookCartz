# Book Cart App
This is the repository for the backend of my proposed online book shopping app where users can shop for books online.
Basically users should be able to create an account, login to that account after being authenticated and also be able to browse for what ever book they want based on the genres they select.
The following endpoints based on certain user stories have been proposed to be created :

ADMIN(baseUrl = "/api/v1/admin")
  1. findById(baseUrl/user/Id) : This endpoint ensures the admins can search for a user as at when required.(Get Mapping, @pathVariable = id)
  2. findAll(baseUrl/user) : This endpoint returns a list of all the current users or registered accounts.(Get Mapping)
  3. deleteById(baseUrl/user/id) : This endpoint gives the admin the power to delete a particular user.(Delete Mapping, @pathVariable = id)
  4. addBook(baserUrl/book) : This endpoint allows the admin to add books as at when necessary.(Post Mapping, @requestBody = bookRequest)
The above endpoints are only accessible to the Admin

USER(baseUrl = "/api/v1/user")
  1. addbookToCart(baseUrl/book) : This endpoint enables users add book to their cart so they can checkout when necessary.(Post Mapping)
  2. findBookById(baseUrl/book/id) : This endpoint enables users search for a particular book in their cart.(Get Mapping, @pathVariable = id)
  3. updateDetails(baseUrl/details/id) : This endpoints helps users update their profile where necessary.(Patch Mapping, @pathVariable = id, @requestBody = updatedUser)
The above endpoints are only accessible to the user

AUTHENTIFICATION(baseUrl = "/api/v1/auth")
  1. register(baseUrl/register) : This enables both users and admins to be able to register for the app.(Post Mapping, @RequestBody = registerRequest)
  2. authentification(baseUrl/authenticate) : This gives users and admins access to the required endpoints(Post Mapping, @RequestBody = authenticationRequest)
The above endpoints are secured hence need no authentifiation

GENERAL(baseUrl = "/api/v1/book")
  1. findBookByGenre(baseUrl/genre) : This endpoint allows both users and admins to check for books according to their genre.(Get Mapping)
  2. findAllBooks(baseUrl) : This endpoints allows both users and admin to look through all the books regardless of genre.

The tables alongside the fields for this project are listed below : 
  1. User Table : Required to store and use users information.
     Parameters
       i.   id(The auto generated id of the user) Type = Long
       ii.  role(The role that is assigned to the user (ADMIN or USER)). Type = Role(an Enum class I created)
       iii. userCart(A list of items inside the users cart. Mapped to the UserCart table) Type = Usercart
       iv.  lastName(The last name of the user). Type = String
       v.   firstName(The first name of the user). Type = String
       vi.  email(The email address of the user). Type = String
       vii. password(The password to be entered by the user). Type = String

  2. Book Table : Required to store and access books.
     Parameters
       i.   id(The auto generated id of the user). Type = Long
       ii.  name(The name of the book). Type = String
       iii. genre(The genre of the book). Type = String
       iv.  quantity(The amount of book available for sale). Type = Integer
       v.   price(The cost of the books). Type = BigDecimal

  3. UserCart : Required to keep track of books users intend to buy.
     Parameters
       i.   id(The auto generated id of the user). Type = Long
       ii.  user(The id of the user the cart belongs to). Type = Long
       iii. bookName(The name of the book in the cart). Type = String
       iv.  quantity(The amount of a particular book present in the users cart). Type = Integer
       v.   price(The cost of the book added to the cart). Type = BigDecimal
