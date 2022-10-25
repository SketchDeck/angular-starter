# SketchDeck project - getting started with Angular

Welcome! This is our little test-project, which outlines the requirements for getting started
with Angular in a way that is relevant to the work we do at SketchDeck with some modifications and additions along the way :)

You'll be invited to our Slack channel to ask any questions you may have and get help if needed.  Please don't hesitate to ask questions if you have any!

The goal of this exercise is to leverage the existing Angular documentation and *Tour of Heroes* tutorial
to create your own new web-app with specific requirements (outlined below).

## Steps
1. Follow the [Angular docs to setup your local application](https://angular.io/guide/setup-local)
_**Note**_: This exercise is to *do the setup* i.e. you should **not** _"TRY ANGULAR WITHOUT LOCAL SETUP"_

![Alt](/no-without-local.png)

2. When you get to _"Create a workspace and initial application"_ (as in screen shot below), **STOP** and follow step 3 (below) _first_.  You'll use the repo you create to create your workspace and initial application (Angular does not include this step - it is required for this project).

![Alt](/create-workspace.png)

3. Creating a repo

You'll need to create a Github repository for your Angular application. This is so that we can review your project together on completion. [Here are the docs](https://docs.github.com/en/get-started/quickstart/create-a-repo) for how to do this if you need help. Make sure to setup the repository as **Public** so that we don't have to jump through hoops for the team to get access to it (just don't put anything private in your repo!)

After creating the repo, clone it to your local dev machine - create your angular app there.

4. After you've got your repo cloned to your local dev machine, continue with creating your Angular app... but instead of going back to the doc above, go to the _"Tour of Heros"_ tutorial and [start here where they create that app](https://angular.io/tutorial/toh-pt0#create-a-new-workspace-and-an-initial-application) and setup your app in your new repo. Feel free to choose whatever defaults you're most comfortable with.

5. Complete all of the steps in [part 1, _"The Hero editor"_](https://angular.io/tutorial/toh-pt1) in the _"Tour of Heros"_ tutorial

6. After completing all of the steps in part 1, _"The Hero editor"_ **skip parts 2 & 3** i.e. do not do part 2, "Display a list" or part 3, "Create a feature component". Instead, go to [part 4, _"Add services"_](https://angular.io/tutorial/toh-pt4) and continue from there **_until_** you get to the _"Get hero data"_ section

![Alt](/get-hero-data.png)

7. Instead, similar to what they've done in the _"Get hero data"_ section (but slightly different), import the `Hero` interface into your service, create a `getHeros` function and return an array, like this:

```
getHeros(): Hero[] {
    return [
      { id: 12, name: 'Dr. Nice' },
      { id: 13, name: 'Bombasto' },
      { id: 14, name: 'Celeritas' },
      { id: 15, name: 'Magneta' },
      { id: 16, name: 'RubberMan' },
      { id: 17, name: 'Dynama' },
      { id: 18, name: 'Dr. IQ' },
      { id: 19, name: 'Magma' },
      { id: 20, name: 'Tornado' }
    ]
  }
```

8. Next do the [_"Provide the HeroService"_ section](https://angular.io/tutorial/toh-pt4#provide-the-heroservice). Stop before trying _"See it run"_

![Alt](/provide-svc.png)

9. Change `heroes.component.html` to match this:
```
<h2>Heros</h2>

<div *ngFor="let hero of heroes">
  <div><span>id: </span>{{hero.id}}</div>
  <div><span>name: </span>{{hero.name}}</div>
</div>
```

Then save and your app in browser should look like this:

![Alt](/hero-list.png)

10. Next, add a `getHero` function in your service that takes one `id` parameter e.g. `getHero(id: number)`. Write this function to pull data from our API for the given id passed in. You'll need to make an HTTP GET request to `https://app.sketchdeck.com/api/hero?id=[the-hero-id]` (replace `[the-hero-id]` with the actual id e.g. `https://app.sketchdeck.com/api/hero?id=12`). What will be returned on success will be an object like this:
```
{
	"id": "12",
	"name": "Dr. Nice",
	"age": "20"
}
```

Now modify your `heroes.component.ts > getHeroes` function to call your new function for this array of ids: `const heroIds = [12, 13, 14, 15, 16, 17, 18, 19, 20]`

You'll need to add `age` to your Hero interface like this:
```
export interface Hero {
  id: number;
  name: string;
  age: number;
}
```
and template:
```
<h2>Heros</h2>

<div *ngFor="let hero of heroes">
  <div><span>id: </span>{{hero.id}}</div>
  <div><span>name: </span>{{hero.name}}</div>
  <div><span>age: </span>{{hero.age}}</div>
</div>
```

And end result should be just like the previous list but with the hero's age added in :) 

11. Push your finalized code to your code repo.

That's it, you're done 🎉

Next step is to schedule a review! Email `joe.teibel@sketchdeck.com` or DM me on Slack, send your Github repo link and let me know you're ready to schedule your review.

The following extra credit is here if the above took you only a couple of hours or less - please don't feel you need to do this!  

Extra credit:
- Style the UI to look nicer
- Create another component that will display the hero's details when selected from a list
- Agument the data set with photos and display those as well!
