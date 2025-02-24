# multi_counter_implicit_gesture

Project where the `DeepObservable` state manager is tested implicitly.

```dart
class _MyRowCounterState extends State<MyRowCounter> {
  @override
  Widget build(BuildContext context) {
    MyCounterProvider provider = context.deepGet<MyCounterProvider>();
    DeepObservable<int> observable = provider.counters[widget.identifier];

    return Padding(
      padding: const EdgeInsets.symmetric(vertical: 10, horizontal: 15),
      child: Container(
        decoration: BoxDecoration(
          color: Colors.grey.withOpacity(0.5),
          borderRadius: BorderRadius.circular(10),
        ),
        child: Padding(
          padding: const EdgeInsets.all(10.0),
          child: Row(
            mainAxisAlignment: MainAxisAlignment.spaceBetween,
            children: [
              Text(
                'Counter ${widget.identifier + 1}:',
                style: TextStyle(fontWeight: FontWeight.w500, fontSize: 15),
              ),
              Text(
                '${observable.reactiveValue(context)}',
                style: TextStyle(fontWeight: FontWeight.w600, fontSize: 20),
              ),
              Row(
                children: [
                  MyIconButton(
                    Icons.remove,
                    onTap: () {
                      provider.decrementCounter(widget.identifier);
                    },
                  ),
                  SizedBox(width: 10),
                  MyIconButton(
                    Icons.add,
                    onTap: () {
                      provider.incrementCounter(widget.identifier);
                    },
                  ),
                ],
              ),
            ],
          ),
        ),
      ),
    );
  }
}
```

- [Deep Observer](https://github.com/carlosparra1998/deep_observer)
