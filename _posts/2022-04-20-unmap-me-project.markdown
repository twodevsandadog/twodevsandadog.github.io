---
layout: post
title: "UnMap Me Design Document"
date: 2022-04-20 14:00:00 +0200
summary: Working through the design of Unmap.me application
published: true
---

# Unmap Me

## Context

A major service or use case of the internet is to enable users to find things in the physical world that they are looking for. The biggest applications used for this right now are Google, Google Maps, Apple Maps, I will refer to these as mapped-based applications. These work great for finding a general assortment of establishments and locations and every location includes types of information that applies to all locations (description, phone number, website, open hours). What these applications do not do well is provide information specific to the different types of locations. For example, if the location is a clothing store, what is the price point? Do they provide clothes for men, women, children? Plus sizes?

As a conseqence these platforms are great for seeing where a location is and how 'good' a random demographic consider the location (0-5 star reviews). What they are not good at is providing useful information specific to the type of location that it is.

There are some applications for more niche location finding - [HappyCow](HappyCow.net) being a good example. HappyCow.net provides locations and details only for restaurants with vegan and vegetarian options. There are also small examples such as the 'Store Locator' features on company websites; [Lowes Store Finder](https://www.lowes.com/store/).

## Problem Summary

There is an opportunity here, in between the Google Maps use case and the niche location finders. Google Maps has great UX, but not great niche location information. Other mapped based applications have great niche location information, but not good user experience and they are complicated and expensive to develop. There are other communities out there as well who need to document locations specific to their community but the only tool they have are creating a google map and putting points on it, which doesn't solve the whole use case from an information and permissions standpoint.

To summarize:

- Google maps is not good at finding niche types of locations, with information specific to a domain
- Niche location finding applications are hard to develop and often have bad UX
- Location based communities don't have a good way to store and share databases of locations

## Solution Summary

The proposed solution to these three problems is a map based application framework called UnMap.me. Through UnMap.me you can create a niche-specific map based application, define a specification for the information that needs to be saved for those locations, then start adding and viewing those locations inside of your niche.unmap.me application.

For example if I wanted to start a map based application for the best kebab places in the city, I could go to unmap.me and go through a series of steps to select the unmap name, define information for kebab places (name, open times, self baked wraps, felafel available), and create my own kebab.unmap.me. Then I could add locations to that application with the relevant information for others to see.

## Use Cases

These use cases will be separated between different launch milestones. Any that do not yet fit into a planned milestone will go in the Beyond section.
There are a few user types here that will be explained later in the Permissions section.

General:

- As a user I can register on unmap.me
- As a registered user I can create a new unmap application for a new type of location, and become an admin for that unmap
- As a user I can go to an existing public unmap and view all of the locations
- As a registered user with access to a private unmap, I can view a map of locations and click into each to view more information
- As a user with access to an unmap, I can move a map around to see locations in other parts of the world
- As a user with access to an unmap, I can search for locations given keywords or regions of the world

Admin:

- As an admin for a unmap, I can define and edit the information needed for each location in that unmap
- As an admin for a unmap I can add locations with domain specific information to that unmap
- As an admin for a unmap I can make my unmap private or public
- As an admin for a private unmap I can invite other users to join to view locations

### MVP

### Beta

### Beyond

## Design Specifications

### Data Model
In general, there are roughly three main types of data:

- Users
- UnMaps
- Locations

#### User
A user is a pretty basic, it has the following pieces of data:

- A username
- A name
- An email address

There will be additional details, like password hashes and what not, that will likely be delegated to AWS Cognito.

#### UnMaps
An UnMap represents a collection of locations that all share some common elements. They will need the following data:

- A name
- A slug (used for the url, i.e. is the slug is `kebab`, then the url would be `kebab.unmap.me`)
- A description
- A "Location Data Model"

##### Location Data Model
A Location Data Model (LDM) is the definition of what attributes an UnMap captures for all locations defined within it. In essence, the LDM is a list of "Attributes", where an attribute has the following fields:

- A name
- A type (i.e. `checkbox`, `list`, `text`, `selection`, `multi-selection`)
- A type-specific definition (as necessary, for example a `selection` would contain a list of options to choose from)
- A description of the field
- Whether or not the field is required, and whether there is a sane default.

#### Location
A Location belongs to an UnMap and will contain metadata about the location, in addition to a populated "Location Data Model". The fields are as follows:

- An unmap
- A name
- An address
- Coordinates (determined automatically)
- A populated LDM that follows the definition in the UnMap.

### Permissions

### Front End / Application

#### Technology

#### Designs

### Backend / Service

## FAQ

## Appendix

This is where I will document and detail information that is less central to the design as a whole and more specific to individual parts. This way I can refer to categories in this section for details when they would be a distraction in earlier parts of the document.

### UX for Map Based Applications

Part of the problem statement is that map based applications for niche applications often have a bad user experience. If this is true, and UnMap.me is meant to address this, we need to identify what 'good' and 'bad' UX in a map based application means exactly. While the MVP of this application cannot and should not have all of the features of something like Google Maps, it can be developed in a way that feels easy to use in mobile and in a browser from the start.

#### UX Problems with existing niche map based applications

#### User Experience Requirements
