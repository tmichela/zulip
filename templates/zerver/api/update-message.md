# Edit a message

{generate_api_description(/messages/{message_id}:patch)}

## Usage examples

{start_tabs}
{tab|python}

{generate_code_example(python)|/messages/{message_id}:patch|example}

A helper method `move_topic` makes it convenient to move messages across `topics` and
`streams`. Arguments are:

stream: str
    Name of the old stream

new_stream: str
    Name of the new stream

topic: str
    Name of the old topic

new_topic: str, optional
    Name of the new topic (same as old topic if not provided)

message_id: int, optional
    Use to select part of the messages in a topic (see propagate_mode). Default
    behavior selects the last message in the topic

propagate_mode: str, optional, default: 'change_all'
    Affect all messages in the topic: 'change_all'
    Affect selected message (message_id): 'change_one'
    Affect all messages after selected message: 'change_after'

notify_old_topic: bool, default: True

notify_new_topic: bool, default: True

```python
    # move all messages from topic 'Slot' in stream 'Danemark' to topic 'Slott' in
    # stream 'Sweden'
    result = client.move_topic('Denemark', 'Sweden', 'Slot', 'Slott')
```

{tab|js}

More examples and documentation can be found [here](https://github.com/zulip/zulip-js).

{generate_code_example(javascript)|/messages/{message_id}:patch|example}

{tab|curl}

{generate_code_example(curl, exclude=["stream_id"])|/messages/{message_id}:patch|example}

{end_tabs}

## Permissions

You only have permission to edit a message if:

1. You sent it, **OR**:
2. This is a topic-only edit for a (no topic) message, **OR**:
3. This is a topic-only edit and you are an admin, **OR**:
4. This is a topic-only edit and your realm allows users to edit topics.

## Parameters

{generate_api_arguments_table|zulip.yaml|/messages/{message_id}:patch}

## Response

#### Example response

A typical successful JSON response may look like:

{generate_code_example|/messages/{message_id}:patch|fixture(200)}

A typical JSON response for when one doesn't have the permission to
edit a particular message:

{generate_code_example|/messages/{message_id}:patch|fixture(400)}
