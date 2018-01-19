## Potential "Dev Housekeeping & Upkeep" track  - ([edit](https://github.com/BriceShatzer/dev_Housingkeeping_and_upkeep_track/edit/master/README.md))

### Feature Switch Cleanup  
- Confirm assumptions about who is actually using feature switches
- Go through stale switches, track down their original purpose, and if they are still needed.
- Update the `/features` page to make management of switches on individual sites easier. 
- Create feature switch Slack bot to periodically remind people to clean up, take stock of total counts, etc.

### Documentation 
- Expand and correct existing documentation, integrating:  
    + [Kinja Walkthrough](https://docs.google.com/presentation/d/1CeO6gllCepM9zffDP1SOXLTmYqbj4QmyqD0n1pDmWf0/)  
    + [Regnerating snapshots for jest tests](https://fusionmediagroup.slack.com/archives/C29GNJC20/p1510679372000219)  
    + [cloudinary image transformations](https://cloudinary.com/documentation/image_transformations)
    + move [On-Call Guide](https://docs.google.com/document/d/1x0kY03zRy2uLET7nRSC9wEHneQwLU-ZGsLplmm2jnb4/edit?usp=sharing) & [On-Call Presentation](https://docs.google.com/a/fusion.net/presentation/d/1tPWI2DBah0cE0E6Opihd9meWjor5Pbp7pvmvbDA5bRY/edit?usp=sharing) into docs? 

- **Create a singular, unified documentation source**: setup a single source of information for everything pertaining to kinja. 
    + Housed all within a github wiki (or [independent gollum instance](https://github.com/gollum/gollum)) rather than as markdowns in a repo. Provides better search & navigation. 

- **UI-Kit Improvements** - *depending on react migration timeframe, may be able to completely replace `/ui-kit` with storybook*  
    + Get all the components working in UI-Kit and establish source of truth w/ what design has (sketch version)  
    + Implement the use of the actual templating/logic of the various ui components rather than the mock-ups the exist in `app/views/closure/tiger/page/internals/ui-kit/*`  

- Create/Update "Kitchen Sink" [post](https://gawkerselenium.kinja.com/permanent-test-post-do-not-delete-1787626061) which shows all possible blocknodes in use. Perhaps have it reside on [changelog.kinja.com](https://changelog.kinja.com/) as a post(s) the are permanently in the siderail 

- Create visual Route & Template hierarchy or map  - [something like this?](https://codex.wordpress.org/images/1/18/Template_Hierarchy.png)  

### Specific Code Refactor/Cleanup 

- `app/com/kinja/mantle/template/page/internals/UiKit.scala` vs `app/com/kinja/mantle/template/page/internals/UiKitNew.scala` ?
- Implement `rel="noopener"` in external anchors
- fmg-sdk-4.0.9.js / fmg-sdk-4.0.9.css - not being gzipped 
- jQuery 2.1.1 -> 2.2.4? ....perhaps remove all public-facing jQuery deps in general?
- ~~es6-ify `kinja-mantle/public/javascripts/app/editor/*`~~ will be handled in react rewrite?
- kinja-mantle/public/javascripts/app/editor/engine/scribe.js
    + `runCmd(imageButtonHandler)`  
- build/tiger/scss/components/_post.scss:1444  
```
// TODO: Delete after AB testing is done  
ul.commerce-inset.fake-list {
    margin-bottom: 0;
    margin-top: -20px;
}
```

- public/javscripts/app/editor/aboveHeadline/imageUploadBehavior/es6:29  
```// TODO: Refactor when doing DAP
export function imageFromFileAttributes(fileAttributes) {
```

- defined but never referenced?   
`'templates/tiger/components/forms/editor/image-caption'`  
> public/javascripts/scribe/plugins/images/scribe-plugin-image-replace-placeholder.js:19  
> public/javascripts/scribe/plugins/images/scribe-plugin-commerce-insets-focus.js:16  
> test/scribe/src/plugins/gawkerplugins/plugins/insets/scribe-plugin-insets-focus.es6:16 

- Dead code?
    + `public/javascripts/lib/scribe/plugins/scribe-plugin-link-prompt-command.js`  
    is now handled by  
    `public/javascripts/view/modal/editor/modal.editor.linkInsertView.js`
