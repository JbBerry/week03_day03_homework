### Tasks

1. Draw a diagram of the application architecture detailing the views and models.
2. Draw a diagram of the event and data flow through the application, detailing the publishing and subscribing with the data being passed between components.

### Questions
#### 1. What the model `Animals` responsible for?

  `Animals.js` holds the information about each animal. It publishes this information on the channel `Animals:selected-animal-ready` which is subscribed by `select_view.js` to provide content for the dropdown box.

  It is also responsible for publishing on the channel `Animals:selected-animal-ready` which is subscribed by `animal_info_view.js` to provide content to the `info-paragraph` element.

#### 2. What is the view `SelectView` responsible for?

  `select_view.js` listens for the user input on the `animals-dropdown` this is published on the `SelectView:change` channel. This is used by `animals.js` to in-turn pass information to `animal_info_view.js`.

#### 3. What does the `SelectView`s populate method do?

  `populate` is passed the argument `allAnimals` containing the array of `animals` from `animals.js`. This information is used to populate the dropdown box `animals-dropdown`

#### 4. What is the view `AnimalInfoView` responsible for?

  `animal_info_view.js` subscribes to `Animals:selected-animal-ready` from `animals.js`. It creates the element `infoParagraph` and uses the object passed to it to populate the elements text content. This new element is then appended to the DOM.

#### 5. What is `app.js` responsible for?

  `app.js` instantiates the objects `animalDropdown`, `animalInfoDisplay` and `animalsDataSource` from their respective classes and binds events to them so they can be interacted with.
