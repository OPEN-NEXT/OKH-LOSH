# [1. File](https://w3id.org/oseg/ont/okh#File)

* [**comment**](http://www.w3.org/2000/01/rdf-schema#comment) "A file that forms part of the project, specified/located either by a URL (okh:url) or a repo-/project-relative path (okh:relativePath)."
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "File"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [1.1. AuxiliaryFile](https://w3id.org/oseg/ont/okh#AuxiliaryFile)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [File](https://w3id.org/oseg/ont/okh#File)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "auxiliary file (neither source nor export)"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [1.2. BoM](https://w3id.org/oseg/ont/okh#BoM)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [File](https://w3id.org/oseg/ont/okh#File)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Bill of Materials"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [1.3. ContributionGuide](https://w3id.org/oseg/ont/okh#ContributionGuide)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [File](https://w3id.org/oseg/ont/okh#File)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Contribution Guide"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [1.4. ExportFile](https://w3id.org/oseg/ont/okh#ExportFile)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [File](https://w3id.org/oseg/ont/okh#File)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "exported source file"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [1.5. Image](https://w3id.org/oseg/ont/okh#Image)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [File](https://w3id.org/oseg/ont/okh#File)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Image"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [1.6. ManifestFile](https://w3id.org/oseg/ont/okh#ManifestFile)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [File](https://w3id.org/oseg/ont/okh#File)
* [**comment**](http://www.w3.org/2000/01/rdf-schema#comment) "file holding the metadata"
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "manifest file"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [1.7. ManufacturingInstructions](https://w3id.org/oseg/ont/okh#ManufacturingInstructions)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [File](https://w3id.org/oseg/ont/okh#File)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Manufacturing Instructions"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [1.8. Readme](https://w3id.org/oseg/ont/okh#Readme)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [File](https://w3id.org/oseg/ont/okh#File)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Readme"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [1.9. SourceFile](https://w3id.org/oseg/ont/okh#SourceFile)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [File](https://w3id.org/oseg/ont/okh#File)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "source file"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [1.10. UserManual](https://w3id.org/oseg/ont/okh#UserManual)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [File](https://w3id.org/oseg/ont/okh#File)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "User Manual"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

# [2. Component](https://w3id.org/oseg/ont/okh#Component)

* [**comment**](http://www.w3.org/2000/01/rdf-schema#comment) "Either a module (MOSH) or Part (POSH); more component types may be added in the future"
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Component"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [2.1. Module](https://w3id.org/oseg/ont/okh#Module)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [Component](https://w3id.org/oseg/ont/okh#Component)
* [**comment**](http://www.w3.org/2000/01/rdf-schema#comment) "Module of Open Source Hardware (MOSH)"
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Module"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [2.2. Part](https://w3id.org/oseg/ont/okh#Part)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [Component](https://w3id.org/oseg/ont/okh#Component)
* [**comment**](http://www.w3.org/2000/01/rdf-schema#comment) "Piece of Open Source Hardware (POSH)"
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Part"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [2.3. Software](https://w3id.org/oseg/ont/okh#Software)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [Component](https://w3id.org/oseg/ont/okh#Component)
* [**comment**](http://www.w3.org/2000/01/rdf-schema#comment) "Software (including firmware) needed to run & use the OSH"
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Software"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

# [3. Reference](https://w3id.org/oseg/ont/okh#Reference)

* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "unambiguous reference"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [3.1. ComponentReference](https://w3id.org/oseg/ont/okh#ComponentReference)

* [**deprecatedOn**](http://creativecommons.org/ns#deprecatedOn) 2023-08-19
* [**deprecated**](http://www.w3.org/2002/07/owl#deprecated) true
* [**comment**](http://www.w3.org/2000/01/rdf-schema#comment) "
    others shall be able to identify/procure this component only by the given reference(s),
    MOSH → URL to corresponding release
    POSH → URL to containing folder
    STD  → standard designation (preferably naming the _latest_ standard)
    BUY  → unambiguous reference"
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Component Reference"
* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [Reference](https://w3id.org/oseg/ont/okh#Reference)
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

### [3.1.1. FileUrl](https://w3id.org/oseg/ont/okh#FileUrl)

* [**supersededBy**](http://schema.org/supersededBy) [File](https://w3id.org/oseg/ont/okh#File)
* [**deprecatedOn**](http://creativecommons.org/ns#deprecatedOn) 2023-07-11
* [**deprecated**](http://www.w3.org/2002/07/owl#deprecated) true
* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [URL](http://schema.org/URL)
* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [ComponentReference](https://w3id.org/oseg/ont/okh#ComponentReference)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "permanent URL to file"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [3.2. WebsiteUrl](https://w3id.org/oseg/ont/okh#WebsiteUrl)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [URL](http://schema.org/URL)
* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [Reference](https://w3id.org/oseg/ont/okh#Reference)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Website URL"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

# [4. http://schema.org/URL](http://schema.org/URL)


## [4.1. FileUrl](https://w3id.org/oseg/ont/okh#FileUrl)

* [**supersededBy**](http://schema.org/supersededBy) [File](https://w3id.org/oseg/ont/okh#File)
* [**deprecatedOn**](http://creativecommons.org/ns#deprecatedOn) 2023-07-11
* [**deprecated**](http://www.w3.org/2002/07/owl#deprecated) true
* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [URL](http://schema.org/URL)
* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [ComponentReference](https://w3id.org/oseg/ont/okh#ComponentReference)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "permanent URL to file"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [4.2. WebsiteUrl](https://w3id.org/oseg/ont/okh#WebsiteUrl)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [URL](http://schema.org/URL)
* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [Reference](https://w3id.org/oseg/ont/okh#Reference)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Website URL"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

# [5. http://ns.nature.com/terms/Publication](http://ns.nature.com/terms/Publication)


## [5.1. Publication](https://w3id.org/oseg/ont/okh#Publication)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [Publication](http://ns.nature.com/terms/Publication)
* [**comment**](http://www.w3.org/2000/01/rdf-schema#comment) "_scientific_ (that is: peer reviewed) publication that _contains_ the design files"
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Scientific Publication"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

