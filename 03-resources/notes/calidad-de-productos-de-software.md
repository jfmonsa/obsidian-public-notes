---
mocs:
    - "[[public-notes/03-resources/uni-courses.moc.md|Uni Courses]]"
tags:
    - uni/courses
    - lang-es
---

# Architecture ?
> Architecture is not only how to organize the files in the project, it goes beyond that.

+ A good architecture splits responsibilities. A file or a function should be responsible for only one thing and does not care what other files or functions do.
+ Defines the foundation of your application
+ encompasses how different parts of the application interact with each other, making it crucial for building scalable and maintainable apps

+ Architectures enforces separation of concerns
+ Cada una de estas layers se preocupa por una cierta cosa, independientes entre si

**Nota**:
para el proyecto sobre el cual trabajamos esta materia:
+ Para el back se implementa la arquitectura ==MVC==
	+ [[mvc-api-rest]]
+ Para el front se implementa la arquitectura ==clean==
	+ [[arquitectura-clean-frontend]]

# Modelo CMMI

-------
Indice (de diapositivas)
2. Que es CMMI ?
3. Objetivos de CMMi
4. Representación
5. Niveles de Madurez

## ¿Que es CMMI?
+ Capability Maturity Model integration (Integración de modelos de madurez de capacidades)
+ Es un modelo (framework) para la mejora y evaluación de procesos para el desarrollo, mantenimiento y operación de sistemas de software
+ CMMI ayuda a organizaciones a cumplir las necesidades de sus clientes, crear valor para inversores y mejorar la calidad del producto y el crecimiento en el mercado
+ CMMI prende ser usado para guiar la mejora de procesos en un proyecto, división o una organización completa
(Otros datos)
+ Administrado por el instituto CMMI, se desarrolló en la universidad de Carnegie Mellon (CMU)
+ succesor de CMM 
+ Este modelo es requerido por muchos contratos del departamento de defensa de Estados Unidos y del gobierno de estados unidos (Especialmente en el desarrollo de software)

## Breve Reseña Historica (?)
The CMMI was developed to combine multiple business maturity models into one framework. It was born from the Software CMM model developed between 1987 and 1997. CMMI Version 1.1 was released in 2002, followed by Version 1.2 in 2006, and Version 1.3 in 2010; V1.3 was replaced by V2.0 in March 2018.
+ Every iteration of the CMMI aims to be easier for businesses to understand and use than the last
### CMMI (V2.0)
+ Version 2.0 also integrates better with agile and Scrum processes pero con un enfoque en seguridad
+ Performance benchmarks and goals outlined in the CMMI can help businesses ensure all projects and processes are cost-effective or profitable

### CMMI V3.0
+ CMMI Version 3.0 was published in 2023


(Entonces retomando aquí ...)
## Objetivos de CMMI
1. Satisfacer las necesidades y expectativas de los clientes.
2. Creación de valor para los inversores/accionistas.
3. Incremento del crecimiento del mercado.
4. Mejora de la calidad de los productos y servicios.
5. Mejora de la reputación en la industria.

(Pero estos objetivos estan dividos por...)
## Representación CMMI

+ In version 1.3 CMMI existed in two representations: continuous and staged
+ In version 2.0 the above representation separation was cancelled and there is now only one cohesive model
Una representación permite que una organización persiga un conjunto diferente de objetivos de mejora. Existen dos representaciones para CMMI:

## Evaluación != certificación
+ An organization cannot be certified in CMMI; instead, an organization is _appraised_. Depending on the type of appraisal, the organization can be awarded a maturity level rating (1–5) or a capability level achievement profile.
+ Many organizations find value in measuring their progress by conducting an appraisal. Appraisals are typically conducted for one or more of the following reasons:
	+ To determine how well the organization's processes compare to CMMI best practices, and to identify areas where improvement can be made
	+ To inform external customers and suppliers of how well the organization's processes compare to CMMI best practices
	+ To meet the contractual requirements of one or more customers

Appraisals of organizations using a CMMI model must conform to the requirements defined in the Appraisal Requirements for CMMI (ARC) document
+ There are three classes of appraisals, A, B and C,

-----
+ Muchas organizaciones valoran el medir su progreso llevando a cabo una evaluación (appraisal) y ganando una clasificación del nivel de madurez o de un nivel de capacidad de logro. Este tipo de evaluaciones son realizadas normalmente por una o más de las siguientes razones:
	+ Para determinar que tan bien los procesos de la organización se comparan con las mejores prácticas CMMI y determinar qué mejoras se pueden hacer.
	+ Como requisito del cliente en licitaciones públicas o concursos privados
+ El Standard CMMI Appraisal Method for Process Improvement (SCAMPI) es el método oficial del (SEI, Instituto de Ingeniería de Software del Gobierno Federal de EEUU)
## Niveles de Madurez CMMI
> For businesses that embrace CMMI, the goal is to raise the organization up to Level 5, the “optimizing” maturity level. Once businesses reach this level, they aren’t done with the CMMI. Instead, they focus on maintenance and regular improvements.

CMMI defines the following five maturity levels (1 to 5) for processes: Initial, Managed, Defined, Quantitatively Managed, and Optimizing

1. ****Maturity level 1 : Initial****
    - processes are poorly managed or controlled.
    - unpredictable outcomes of processes involved.
    - ad hoc and chaotic approach used.
    - No KPAs (Key Process Areas) defined.
    - Lowest quality and highest risk.
2. ****Maturity level 2 : Managed****
    - requirements are managed.
    - processes are planned and controlled.
    - projects are managed and implemented according to their documented plans.
    - This risk involved is lower than Initial level, but still exists.
    - Quality is better than Initial level.
3. ****Maturity level 3 : Defined****
    - processes are well characterized and described using standards, proper procedures, and methods, tools, etc.
    - Medium quality and medium risk involved.
    - Focus is process standardization.
4. ****Maturity level 4 : Quantitatively managed****
    - quantitative objectives for process performance and quality are set.
    - quantitative objectives are based on customer requirements, organization needs, etc.
    - process performance measures are analyzed quantitatively.
    - higher quality of processes is achieved.
    - lower risk
5. ****Maturity level 5 : Optimizing****
    - continuous improvement in processes and their performance.
    - improvement has to be both incremental and innovative.
    - highest quality of processes.
    - lowest risk in processes and their performance.
## CMMI Model - Capability Levels
- **Capability Level 0 – Incomplete:** Inconsistent performance and an “incomplete approach to meeting the intent of the practice area.”
- **Capability Level 1 – Initial:** The phase where organizations start to address performance issues in a specific practice area, but there is not a complete set of practices in place.
- **Capability Level 2 – Managed:** Progress is starting to show and there is a full set of practices in place that specifically address improvement in the practice area.
- **Capability Level 3 – Defined:** There’s a focus on achieving project and organizational performance objectives and there are clear organizational standards in place for addressing projects in that practice area.
## Conclusion (?)
> CMMI provides a structured approach to process improvement, ensuring higher quality and lower risk in organizational processes. By following the staged or continuous representation, organizations can achieve different maturity or capability levels, leading to standardized, managed, and optimized processes. This systematic improvement enhances customer satisfaction, market reputation, and overall business performance. CMMI is a valuable tool for organizations seeking to integrate and enhance their processes effectively.

## Dudas?
+ Diferencia entre niveles de madures y niveles de capacidad
## Donde Aplicar
+ 

## Referencias
1. https://es.wikipedia.org/wiki/Capability_Maturity_Model_Integration
2. https://www.geeksforgeeks.org/capability-maturity-model-integration-cmmi/
3. https://www.cio.com/article/274530/cmmi-explained.html
4. https://en.wikipedia.org/wiki/Capability_Maturity_Model_Integration#cite_note-Go08-3