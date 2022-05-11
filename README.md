# hokya
GlossaryItem.cs namespace Glossary
{
public class GlossaryItem
{
public string Term { get; set; } public string Definition { get; set; }
}
}
2)	D:\Glossary\Controllers\ GlossaryController.cs (type it in notepad and save as all files)
//Controllers/GlossaryController.cs using System;
using System.Collections.Generic; using Microsoft.AspNetCore.Mvc; using System.IO;
namespace Glossary.Controllers
{
[ApiController] [Route("api/[controller]")]
public class GlossaryController: ControllerBase
{
private static List<GlossaryItem> Glossary = new List<GlossaryItem> { new GlossaryItem
{
Term= "HTML",
Definition = "Hypertext Markup Language"
},
 
new GlossaryItem
{
Term= "MVC",
Definition = "Model View Controller"
},
new GlossaryItem
{
Term= "OpenID",
Definition = "An open standard for authentication"
}
};

[HttpGet]
public ActionResult<List<GlossaryItem>> Get()
{	return Ok(Glossary);
}

[HttpGet] [Route("{term}")]
public ActionResult<GlossaryItem> Get(string term)
{
var glossaryItem = Glossary.Find(item =>
item.Term.Equals(term, StringComparison.InvariantCultureIgnoreCase));

if (glossaryItem == null)
{	return NotFound();
} else
{
return Ok(glossaryItem);
}
}

[HttpPost]
public ActionResult Post(GlossaryItem glossaryItem)
{
var existingGlossaryItem = Glossary.Find(item =>
item.Term.Equals(glossaryItem.Term, StringComparison.InvariantCultureIgnoreCase));

if (existingGlossaryItem != null)
{
return Conflict("Cannot create the term because it already exists.");
}
else
{
Glossary.Add(glossaryItem);
var resourceUrl = Path.Combine(Request.Path.ToString(), Uri.EscapeUriString(glossaryItem.Term)); return Created(resourceUrl, glossaryItem);
}
}
[HttpPut]
public ActionResult Put(GlossaryItem glossaryItem)
{
var existingGlossaryItem = Glossary.Find(item => item.Term.Equals(glossaryItem.Term, StringComparison.InvariantCultureIgnoreCase));

if (existingGlossaryItem == null)
{
return BadRequest("Cannot update a nont existing term.");
} else
{
existingGlossaryItem.Definition = glossaryItem.Definition; return Ok();
}
}

[HttpDelete] [Route("{term}")]
public ActionResult Delete(string term)
{
var glossaryItem = Glossary.Find(item =>
item.Term.Equals(term, StringComparison.InvariantCultureIgnoreCase));
 
 Monolithic architecture is built as one large system and is usually one code-base
It is not easy to scale based on demand
It has shared database
Large code base makes IDE slow and build time gets increase.
It extremely difficult to change technology or language or framework because everything is tightly coupled and depend on each other
Microservices architecture is built as small independent module based on business functionality
t is easy to scale based on demand.
Each project and module has their own database
Each project is independent and small in size. So overall build and development time gets decrease.
Easy to change technology or framework because every module and project is independent


Characteristics of a Microservice Architecture
Componentization via Services. ...
Organized around Business Capabilities. ...
Products not Projects. ...
Smart endpoints and dumb pipes. ...
Decentralized Governance. ...
Decentralized Data Management. ...
Infrastructure Automation. ...
Design for failure.


5 core components of microservices architecture
Microservices. Microservices make up the foundation of a microservices architecture. ...
Containers. ...
Service mesh. ...
Service discovery. ...
API gateway.


Here are five elements that your microservice will need before it can take its place in a distributed application architecture.
Properly scoped functionality. ...
Presenting an API. ...
Traffic management. ...
Data offloading. ...
Monitoring.

What is the goal of microservices?
The microservice architecture structures an application as a set of small, loosely coupled services. 
As a result, it improves the development time attributes – maintainability, testability, deployability, etc.
 – and enables an organization to develop better software faster.

if (glossaryItem == null)
{	return NotFound();
}
else
{		Glossary.Remove(glossaryItem); return NoContent();
}
}
}
}
