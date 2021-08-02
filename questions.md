## Interview questions

(Everything is inside App.vue)

#### AppBasic

The app gets a list of dogs from the passed in URL when it is first mounted. There are currently two filters that change the genderFilter and breedFilter variables in the data(), but they do not change the rendered list of dogs yet. How would you implement? 

#### AppMedium

I don't like this idea... It requires we start here then go to the "basic" version. Think of something else.
<!-- Redo the filters as methods that trigger with event values, which manually manipulates the data().dogs array. Ask how this could be improved. -->

#### AppAdvanced

(Add back in the favorite icon from the previous commit)

A new feature request! When you click the "favorite" icon, it shows that dog at the top of your list, even if it should be filtered out by breed/gender.