---
title: UniRx observable reference
author: johan
typora-root-url: ..
github_comment_id: 5
---

[UniRx](https://github.com/neuecc/UniRx) is a great reactive programming library for Unity. However, I found it a bit difficult to write a clean reusable and decoupled user interface, so I wrote a small add-on library for UniRX which I think solves the problem quite nicely.

So the problem I was trying to solve is pretty basic. I was writing a score counter and I wanted to write it in such a way that I could re-use it in another project without rewriting any way. In other words I wanted it to be independent of the data model.

Basically I was trying to turn this:

```c#
public class Player : MonoBehaviour
{
    public IObservable<int> ScoreAsObservable { get; set; }
    // ...
}

public class Score : MonoBehaviour
{
    [SerializeField] private Player player;
    void Start()
    {
        player.ScoreAsObservable.SubscribeToText(GetComponent<Text>());
    }
}
```

Into something where the score didn't have to know the details about how the Player works.

What I came up with, was [UniRx Obervable Reference](https://github.com/johanhelsing/unirxobservablereference). It basically works like this:

If you need to expose a plain setter on your UI component, i.e.

```c#
public class SetTextFromInt : MonoBehaviour
{
    [SerializeField] private Text text;
    public SetFromInt(int value) => text.text = value.ToString();
}
```

Now the rest is done with generic components through the Unity inspector :) First, add the component, `Int Observable Listener` 

<img src="/assets/observable-reference-added.png" alt="added the Int Obserable Listener" style="zoom:50%;" />

Then select the game object with the score on it, and a compatible property from the dropdown. You can select any property that is assignable to a `IObservable<int>`. I.e. it doesn't matter if it's a `ReactiveProperty<int>`, or a `IObservable<int>` or a `IntReactiveProperty` property.

<img src="/assets/obserable-reference-select-property.png" alt="select the game object and property" style="zoom:50%;" />

Then, just add a handler to set the value:

<img src="/assets/observable-reference-with-handler.png" alt="image-20200601153407575" style="zoom:50%;" />

And that's it.

Now I can move the score component to another project, and all I have to do, is assign a new `IObservable<int>` property using the inspector.

It can be installed as a upm package. Here is the source: [github.com/johanhelsing/unirxobservablereference](https://github.com/johanhelsing/unirxobservablereference)