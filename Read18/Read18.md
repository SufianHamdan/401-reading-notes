# Read: 18 - Web App Security

**Hibernate Many to Many**
  * This tutorial shows how the @ManyToMany annotation can be used for specifying this type of relationships in Hibernate.
  * Entity Relationship Diagram – which shows the many-to-many association between two entities 
  * Database Setup:
      - created database with the name spring_hibernate_many_to_many
      - create the employee and project tables along with the employee_project join table with employee_id and project_id as foreign keys
      - Once that is setup, preparation of the Maven dependencies and Hibernate configuration needs to be done.
      - Create model classes with JPA annotations. When both classes refer to one another, the association between them is bidirectional. 
      - In order to map a many-to-many association, we use the @ManyToMany, @JoinTable and @JoinColumn annotations.
      - @ManyToMany annotation - is used in both classes to create the many-to-many relationship between the entities. This association has two sides i.e. the owning side and the inverse side.
      - @JoinTable - is used to define the join/link table. 
      - @JoinColumn annotation - is used to specify the join/linking column with the main table. 
      - Execution: write the a JUnit test

**This World of Ours by James Mickens**
  * Its like security researchers have problems with public relations because they make it so you can't just do whatever you want on a website.
  * Security researchers are always trying to combate security issues, and make a better system for people to create passwords that are more secure. No matter what password you use, it can be breached. Its not a good idea to use the same password for everything.
  * The threat model is what security researchers use to combat security breaches by telling people how to make passwords and where the security threats come from, but those security breaches aren't always from obvious places.
  * There is no perfect security system out there, and no matter how strong of a security system it will be eventually broken in to. 
  * Information flow control and security labels are used to make things more secure.
  * Most people don't want to spend a bunch of money just to make there system more secure. So, security researchers should not focus on what would happen, but on what will happen when I properly compile my program.