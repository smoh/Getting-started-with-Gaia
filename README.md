# Getting-started-with-Gaia

Bookmarks to resources about Gaia+

- [Gaia Home](https://www.cosmos.esa.int/web/gaia/home)
- [Gaia Archive](https://gea.esac.esa.int/archive/)
- Datamodel: [DR1](https://gea.esac.esa.int/archive/documentation/GDR1/datamodel/index.html) | [DR2](https://gea.esac.esa.int/archive/documentation/GDR2/Gaia_archive/chap_datamodel/)
- Papers with DR: [DR1](https://www.cosmos.esa.int/web/gaia/dr1-papers) | [DR2](https://www.cosmos.esa.int/web/gaia/dr2-papers)



## Data Access using TAP

### Learn ADQL

- [An ADQL cookbook to accompany Gaia DR1](https://www.gaia.ac.uk/data/gaia-data-release-1/adql-cookbook)
- [ADQL cheatsheet](adql-cheatsheet.md)
- [A collection of snippets](gaia-adql-snippets.md)
- [Cross-matching to Gaia DR2](Cross-matching to Gaia DR2.ipynb)

### TAP Clients

- [A simple TAP interface for python](https://github.com/mfouesneau/tap) with a great tutorial
- [astroquery](https://astroquery.readthedocs.io/en/latest/) has a [TAP module](https://astroquery.readthedocs.io/en/latest/utils/tap.html) and [gaia module](https://astroquery.readthedocs.io/en/latest/gaia/gaia.html)
- [pyvo](http://github.com/pyvirtobs/pyvo) implements TAP service as one of many ways to access VO data services.
- [TOPCAT](http://www.star.bris.ac.uk/~mbt/topcat/) is a full-fledged GUI application for interactive exploration of tabular data with access to _many_ astronomical databases (including Gaia) built-in and much more.


## Cross-matches

- Gaia archive already provides cross-match lookup tables for many surveys as well as the original catalogs of each survey, so one can just `JOIN` on appropriate ID columns.
- Note that some external tables are under `gaiadr1` schema while some under `gaiadr2`.
- [Gaia DR2 + Kepler/K2 cross-matches](http://gaia-kepler.fun) by Megan Bedell [repo](https://github.com/megbedell/gaia-kepler.fun)


## Data manipulation tools

- [astropy.coordinates](http://docs.astropy.org/en/stable/coordinates/) for all kinds of coordinate transformations
- [gaia_tools](https://github.com/jobovy/gaia_tools): Tools for working with the @ESAGaia data and related data sets
- [pyia](https://pyia.readthedocs.io/en/latest/): a Python package for working with data from the Gaia mission

## Parallax to distance



## Dynamics

- [amuse](http://www.amusecode.org): Astrophysical Multipurpose Software Environment. [repo](https://github.com/amusecode/amuse)
- [gala](http://gala.adrian.pw/en/latest/): Galactic and gravitational dynamics in Python. [repo](https://github.com/adrn/gala)
- [galpy](https://galpy.readthedocs.io/en/v1.4.0/): Galactic Dynamics in python. [repo](https://github.com/jobovy/galpy)

## Stellar libraries/isochrones


- Morgan Fouesneu has written small python clients to get isochrone models easily from their websites: [ezmist](https://github.com/mfouesneau/ezmist) | [ezpadova](https://github.com/mfouesneau/ezpadova) | [ezdart](https://github.com/mfouesneau/ezdart)
- [isochrones](https://github.com/timothydmorton/isochrones) provides common interface to isochrone models. Under active development and documentation incomplete at the moment.


## Other surveys
