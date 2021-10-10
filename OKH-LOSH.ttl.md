# [1. Reference](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#Reference)

* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "unambiguous reference"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [1.1. ComponentReference](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#ComponentReference)

* [**comment**](http://www.w3.org/2000/01/rdf-schema#comment) "
    others shall be able to identify/procure this component only by the given reference(s),
    MOSH → URL to corresponding release
    POSH → URL to containing folder
    STD  → standard designation (preferably naming the _latest_ standard)
    BUY  → unambiguous reference"
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Component Reference"
* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [Reference](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#Reference)
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

### [1.1.1. FileURL](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#FileURL)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [URL](http://schema.org/URL)
* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [ComponentReference](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#ComponentReference)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "permanent URL to file"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [1.2. WebsiteURL](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#WebsiteURL)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [URL](http://schema.org/URL)
* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [Reference](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#Reference)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Website URL"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

# [2. http://schema.org/URL](http://schema.org/URL)


## [2.1. FileURL](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#FileURL)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [URL](http://schema.org/URL)
* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [ComponentReference](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#ComponentReference)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "permanent URL to file"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [2.2. WebsiteURL](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#WebsiteURL)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [URL](http://schema.org/URL)
* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [Reference](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#Reference)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Website URL"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [2.3. dataSource](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#dataSource)

* [**cardinality**](http://www.w3.org/2002/07/owl#cardinality) 1
* [**domain**](http://www.w3.org/2000/01/rdf-schema#domain) [Module](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#Module)
* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [URL](http://schema.org/URL)
* [**comment**](http://www.w3.org/2000/01/rdf-schema#comment) "platform, where the crawler found the metadata (e.g. GitHub, Wikifactory)"
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Metadata Source"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [DatatypeProperty](http://www.w3.org/2002/07/owl#DatatypeProperty)

## [2.4. repoHost](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#repoHost)

* [**cardinality**](http://www.w3.org/2002/07/owl#cardinality) 1
* [**domain**](http://www.w3.org/2000/01/rdf-schema#domain) [Module](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#Module)
* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [URL](http://schema.org/URL)
* [**comment**](http://www.w3.org/2000/01/rdf-schema#comment) "platform, where the OSH documentation is located (e.g. GitLab, Wikifactory or any self-hosted website or wiki)"
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Repo Host"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [DatatypeProperty](http://www.w3.org/2002/07/owl#DatatypeProperty)

# [3. Component](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#Component)

* [**comment**](http://www.w3.org/2000/01/rdf-schema#comment) "Either a module (MOSH) or Part (POSH); more component types may be added in the future"
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Component"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [3.1. Module](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#Module)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [Component](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#Component)
* [**comment**](http://www.w3.org/2000/01/rdf-schema#comment) "Module of Open Source Hardware (MOSH)"
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Module"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [3.2. Part](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#Part)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [Component](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#Component)
* [**comment**](http://www.w3.org/2000/01/rdf-schema#comment) "Piece of Open Source Hardware (POSH)"
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Part"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [3.3. Software](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#Software)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [Component](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#Component)
* [**comment**](http://www.w3.org/2000/01/rdf-schema#comment) "Software (including firmware) needed to run & use the OSH"
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Software"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

# [4. File](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#File)

* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "File"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [4.1. BoM](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#BoM)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [File](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#File)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Bill of Materials"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [4.2. ContributionGuide](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#ContributionGuide)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [File](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#File)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Contribution Guide"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [4.3. ExportFile](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#ExportFile)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [File](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#File)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "exported source file"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [4.4. Image](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#Image)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [File](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#File)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Image"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [4.5. ManifestFile](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#ManifestFile)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [File](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#File)
* [**comment**](http://www.w3.org/2000/01/rdf-schema#comment) "file holding the metadata"
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "manifest file"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [4.6. ManufacturingInstructions](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#ManufacturingInstructions)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [File](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#File)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Manufacturing Instructions"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [4.7. Readme](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#Readme)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [File](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#File)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "Readme"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [4.8. SourceFile](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#SourceFile)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [File](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#File)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "source file"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

## [4.9. UserManual](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#UserManual)

* [**subClassOf**](http://www.w3.org/2000/01/rdf-schema#subClassOf) [File](https://github.com/OPEN-NEXT/OKH-LOSH/raw/master/OKH-LOSH.ttl#File)
* [**label**](http://www.w3.org/2000/01/rdf-schema#label) "User Manual"
* [**type**](http://www.w3.org/1999/02/22-rdf-syntax-ns#type) [Class](http://www.w3.org/2002/07/owl#Class)

