<!-- TITLE: How To Approach Software Development? -->
<!-- SUBTITLE: A quick summary of How To Approach Software Development -->

# Interesting Questions
1. which S/W system categories dominate the market? i.e where the money and the jobs tend to be?
2. what S/W skills are needed? 
3. need DB back-end?
4. which programming language?
5. what support tech > tools required?

# Software Dev Paradigms
* focus of different appoach to schedule of different activities involved in Software Development
* no single theoritical model/paradigm actually works in every circumstance.

# Inception
* focus mostly on (but not only)
	* Bussiness modeling 
	* Requirements extraction and analysis
	* Preliminary design

# SD: From art to engineering
## 1.1 S/W systems vs H/W

|S/W Engineer Viewpoint|H/W Engineer Viewpoint|
|:-----------------------------------------------:|:------------------------------------------------------:|
|systems are mostly s/w systems|systems are traditionally h/w systems|
|h/w component is controlled through standard interfacing protocols|s/w are either not existing or not extremely relevent|

* Until few years ago, computing foccussed on data processing systems.
* H/W were limited to the standard I/O devices.
* H/W is currently capable of providing structured data through pluggable software drivers that represent the real interfacing protocol for the system developers.

| H/W Failure curve | S/W (IDEALIZED) Failure curve |
|:-:|:-:|
|![Hwfrc](/uploads/hwfrc.png "Hwfrc")|![Swfrc](/uploads/swfrc.png "Swfrc")|

* **Actual S/W Curve**
* ![Swafrc](/uploads/swafrc.png "Swafrc")
*  S/W engineering/development intriduces **quality** issues/problems based on its complexity (*that do not exist in classic manufacturing.*)
*  S/W is about human things, it changes w.r.t time as a result of continous change.
*  more the messing around with the perfect code, more it has side effects.
*  Constraints are removed due to H/W upgrades in due time.
	*  Eg. Windows XP to Windows 7, 10
* Reusable S/W components allow to concentrate on innovative elements of design. However, most S/W are custom built.

## 1.2 S/W Quality: What?

* Quality of development process that consequences quality of the product.
* S/W development methodologies 'model' the S/W from its specification to its implemention.

## 1.3 S/W

* S/W production has a poor track record of being error/bug free.
* Substantial errors still exists

## 1.4 Factors affecting S/W Quality

* **Complexity:**
	* The problem domain is complex
	* The development process is very difficult to manage
	* A system is now so complex that no single programmer can fully understand all its code

* **Change:**
* A system change to fix a bug causes another bug
* Each change worsens the system structure making the next change even more expensive.
* As time goes on, implementing a change becomes too expensive and the system is no more viable to maintain



