[[python]]
[[pytest]]
[[testing]]
[[unit testing]]
[[logging]]


## caplog fixture

https://docs.pytest.org/en/stable/how-to/logging.html

Inside tests it is possible to change the log level for the captured log messages. This is supported by the `caplog` fixture:


```
def test_foo(caplog):
    caplog.set_level(logging.INFO)
```

Lastly all the logs sent to the logger during the test run are made available on the fixture in the form of both the `logging.LogRecord` instances and the final log text. This is useful for when you want to assert on the contents of a message:

```
def test_baz(caplog):
    func_under_test()
    for record in caplog.records:
        assert record.levelname != "CRITICAL"
    assert "wally" not in caplog.text
```

## -- capture

https://docs.pytest.org/en/stable/how-to/capture-stdout-stderr.html

The `--capture=` command line flag intercepts stdout and stderr. The flag configures reporting, but a pytest fixture can also be used for more granular control.

```
pytest -s                  # disable all capturing
```