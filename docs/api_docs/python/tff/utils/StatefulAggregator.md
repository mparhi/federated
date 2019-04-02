<div itemscope itemtype="http://developers.google.com/ReferenceObject">
<meta itemprop="name" content="tff.utils.StatefulAggregator" />
<meta itemprop="path" content="Stable" />
<meta itemprop="property" content="__call__"/>
<meta itemprop="property" content="__init__"/>
<meta itemprop="property" content="initialize"/>
</div>

# tff.utils.StatefulAggregator

## Class `StatefulAggregator`

Defined in
[`core/utils/computation_utils.py`](http://github.com/tensorflow/federated/tree/master/tensorflow_federated/python/core/utils/computation_utils.py).

A simple container for a stateful aggregation operator.

<h2 id="__init__"><code>__init__</code></h2>

```python
__init__(
    initialize_fn,
    next_fn
)
```

Creates a `StatefulAggregator`.

## Methods

<h3 id="__call__"><code>__call__</code></h3>

```python
__call__(
    state,
    value,
    weight=None
)
```

Performs an aggregate of value@CLIENTS, with optional weight@CLIENTS.

This is a TFF operator intended to (only) be invoked in the context of a
<a href="../../tff/federated_computation.md"><code>tff.federated_computation</code></a>.
It shold be compatible with the TFF type signature `(state@SERVER,
value@CLIENTS, weight@CLIENTS) -> (state@SERVER, aggregate@SERVER).`

#### Args:

*   <b>`state`</b>: A <a href="../../tff/Value.md"><code>tff.Value</code></a>
    placed on the <a href="../../tff.md#SERVER"><code>tff.SERVER</code></a>.
*   <b>`value`</b>: A <a href="../../tff/Value.md"><code>tff.Value</code></a> to
    be aggregated, placed on the
    <a href="../../tff.md#CLIENTS"><code>tff.CLIENTS</code></a>.
*   <b>`weight`</b>: An optional
    <a href="../../tff/Value.md"><code>tff.Value</code></a> for weighting
    values, placed on the
    <a href="../../tff.md#CLIENTS"><code>tff.CLIENTS</code></a>.

#### Returns:

A tuple of <a href="../../tff/Value.md"><code>tff.Value</code></a>s
(state@SERVER, aggregate@SERVER) where * state: The updated state. * aggregate:
The result of the aggregation of `value` weighted by `weight.

<h3 id="initialize"><code>initialize</code></h3>

```python
initialize()
```

Returns the initial state.