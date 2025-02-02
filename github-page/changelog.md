---
title: "Changelog"
layout: single
classes: wide
toc: true
redirect_from:
  - /CHANGELOG
---

<!--Sorry but linking to the issue/pr can only be made so in jekyll without more clutter-->

<!-- 
## 6.1.3

<sub>This Version is not yet released, only changes made until now are listed here</sub>

- Add here
-->

## 6.1.2

- Allow setting `_id: false` (and apply it) for `@mapProp`
- [IC] De-duplicate code for `_id` if subDocument

## 6.1.1

- `deleteModel` now deletes the model from the connection it is on {% include gitissue repo="typegoose" num=119 %}
- [IC] de-duplicate test code for connecting

## 6.1.0

- Update Dependencies
  - Upgrade mongoose from 5.7.1 to 5.7.7
  - [IC] Upgrade Typescript from 3.6.x to 3.7.2
- Completly remove `@staticMethod` & `@instanceMethod`, because they were completly obsolete
- README now has no documentation anymore
- `@prop({ validate })` now accepts `{ validator, message }` as an array
- Add function `deleteModel` & `deleteModelWithClass`
- allow Prop Option "type" to overwrite the inferred type [look here for an example](https://typegoose.github.io/typegoose/docs/decorators/prop/#type)
- integrate "Array Validators & Transform" tests {% include gitissue repo="typegoose" num=29 %}
- adding global options, with `setGlobalOptions`
- add modelOption `runSyncIndexes`
- add modelOption `allowMixed`
- add `text` to PropOptions
- deprecate ArrayPropOptions's `itemsRef`, `itemsRefPath` & `itemsRefType`
- `DocumentType` will now overwrite the type of `_id` if the class is extending `Base` (in typescript there is currently no other way)
- add `tslib` as dependencie to minimize generated code
- fixing typo in (deprecated) `setModelForClass`
- Remake how Enums are handeled, use `setGlobalOptions({ globalOptions: { useNewEnum: true } })` (to not break existing databases made with the old handling)
- add function `getModelWithString`
- [IC] tsconfig: add option "strictBindCallApply"
- [IC] tsconfig: add option "strictFunctionTypes"
- [IC] combine `initAsObject` and `initAsArray` into `initProperty`
- [IC] Use internal "isNullOrUndefined", needed because all "util.is*" functions got deprecated in node 4.0.0
- [IC] Replace all "isArray" with "Array.isArray", needed because all "util.is*" functions got deprecated in node 4.0.0
- [IC] adding many sanity `isNullOrUndefined` checks
- [IC] Re-done how the handling of `Mixed` is done
- [IC] Re-done how `IModelOptions` are merged (thanks to lodash `cloneDeepWith` & `mergeWith`)
- [IC] de-duplicate "ref" & "refPath" code
- [IC] added test for "Custom Types"
- [IC] typegoose now makes use of "importHelpers"(tsconfig) to save some space
- [IC] Refactor how "isPrimitive" works, some types like `Buffer` & `Decimal` now work
- [IC] Added more debug logs to `prop.ts`
- [IC] Move Decorator Cache to the class itself
- [IC] "baseProp" now uses one single arguments, whith all the options
- [IC] "createUniqueID" now returns a boolean instead of the "initname"

## 6.0.4

This Release didnt change anything on the code, it was mostly tests & github-page
- Update Dependencies
  - Upgrade mongoose from 5.7.1 to 5.7.4
- Added soft warning when using "ref" in an "arrayProp"
- Added soft warning when using "refPath" in an "arrayProp"
- Add missing ")" to a deprecation message
- [IC] Fixed some Test's types
- [IC] internal variable renames to better reflect what they are for

## 6.0.3

- when using `@plugin`, options are now checked if they are an object, when not: make them an object
- Added many debug logs for `_buildSchema`
- Added Prop Option `autopopulate`, only has an effect if `mongoose-autopopulate` is used
- Added default class `FindOrCreate` which has the types for `mongoose-findorcreate`

## 6.0.2

- actually allow overwriting "_id" of "Base"
- [IC] add npm version script

## 6.0.1

- Add TSDoc for `refType` on PropOptions
- `refPath` now uses the right type (new uses `refType` instead of `itemsType`)
- Fix decorator options (rawOptions) mutating thanks to {% include gitissue repo="typegoose" num=60 %}
- Pre hook's function's `next` is now not marked as "optional" anymore, which caused `next()` to be `EmptyVoidFn | undefined`

## 6.0.0

[To Migrate, please look at the migration guide]({{ site.baseurl }}{% link _guides/migrate-to-6.md %})

- Project got moved to the new repo (hasezoey/typegoose) and new package `@hasezoey/typegoose`
- rename `InstanceType<T>` to `DocumentType<T>` [{% include gitissue repo="szokodiakos" num=366 %}]
- adding a migration guide from ~5.9 to 6.0.0
- adding missing "get" and "set" property options [{% include gitissue repo="szokodiakos" num=260 %}]
- adding `@modelOptions` and `getModelForClass` and `setModelForClass` will now override it
- `setModelForClass` is now deprecated [{% include gitissue repo="hasezoey" num=6 %}, {% include gitissue repo="szokodiakos" num=186 %}]
- setting the Typegoose Class to abstract
- deprecating the Typegoose Class because of making the functions outsourced [{% include gitissue repo="szokodiakos" num=356 %}]
- hook methods can now be arrays of methods [{% include gitissue repo="szokodiakos" num=313 %}]
- completely removed parallel from pre hook
- refactored the types of hooks
- adding support for any value in prop for plugins [{% include gitissue repo="szokodiakos" num=374 %}]
- `schema.loadClass` is now used instead of `@instanceMethod` and `@staticMethod` [{% include gitissue repo="szokodiakos" num=48 %}, {% include gitissue repo="szokodiakos" num=346 %}, {% include gitissue repo="szokodiakos" num=182 %}]
- method decorators are now deprecated
- schema generation got refactored (/reconstructed) multiple times
- adding `count` to VirtualOptions
- Updated Dependencies (^mongoose@5.7.1)
- adding discriminator support hasezoey#11
- adding default class for (schemaOptions) timestamps
- adding more docs to README & as tsdoc
- some changes that are probably forgot
- szokodiakos#363 got reverted in favor of mongoose@5.6.9
- fixes Custom Options not passed through to mongoose & plugins when using ref [{% include gitissue repo="szokodiakos" num=379 %}]
- Adding "immutable" prop option [{% include gitissue repo="szokodiakos" num=320 %}]
- adding Types to Ref (to allow not just ObjectID) [{% include gitissue repo="szokodiakos" num=369 %}]
- szokodiakos#54 seems to work now in 6.0.0 (added test in 6.0.0-21)
- because of the changes in 6.0.0 #235 got fixed
- Adding "InvalidTypeError" for the case that "undefined" or "null" is used as a type (or something other happenes)
- Change Error text of "InvalidPropError"
- adding some "soft-errors" and traces with "loglevel"
- exposing settings for "loglevel"
- fixes Decorator Execution Order [{% include gitissue repo="hasezoey" num=23 %}, {% include gitissue repo="hasezoey" num=24 %}]
- add support for custom discriminator properties
- add error if using a self-containing class
- add support for using multiple classes with the same name (`automaticName`, `customName`, `collection`)
- [IC] "NoParamConstructor" got renamed into "AnyParamConstructor" it now accepts any arguments
- [IC] Remake data.ts to use Maps hasezoey#3
- [IC] adding many tests and bumping coverage
- [IC] moving many Types to types.ts
- [IC] removing unneeded dependencies
- [IC] changed how travis runs jobs multiple times
- [IC] many tslint rule changes
- [IC] getting the name from "class.name" got outsourced into "utils.getName" (for future use)
- [IC] use switches instead of many if's
- [IC] adding some tests

## 5.9.2

- Change README examples & badges to the new repo
- use new travis.yml (from version 6.0.0)
- use new style of package.json (from version 6.0.0)

- Tags got deleted and added, please remove all local tags and re-download them

This Release did not change anything in the code, it is just there to update the NPM front

## 5.9.1

- fix accidentally added typeguards
- add a note that typegoose uses mongoose's strict by default
- add note that typegoose dosnt work with classes with the same name (at least in 5.x, working on it in 6.x)
- implemented a hack for ObjectId / ObjectID (mongoose some version fixed this)

## 5.9.0

- This should not be a breaking release
- Hooks now support Regular Expression for names, like mongoose
- Tests are splitted into their own files
- Fixing `itemsRefPath` & adding tests
- `itemsRef` now supports to be used with a string as model
- `@prop({ alias })` is now supported
- Index weights are now supported
- `isDocument` & `isDocumentArray` typeguards are now implemented
- Updated Dependencies
  Note worthy are:
  - mongoose 5.6 is now required instead of 5.5
  - this project should be used with typescript 3.5+
- `@mapProp()` is now implemented
- Fix for `@prop({ select })`
- A public version of `buildSchema` is now available
- Added more Documentation to README
- Added TSDOC to many functions and properties
- build target is now ES6 instead of ES5
