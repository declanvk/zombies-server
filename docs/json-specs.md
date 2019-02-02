# From Server to Player

## Player Join Response (3)
Sent from server to player to notify successful room join.

```json
{
    "pkt_name": "player_join_response",
    "room_number": "room number (string)",
    "user_name": "user name (string)",
    "join_status": {
       "status": "success" | "failure",
       "failure_reason": "failure reason (string)"
    }
}
```

## Game Starting (6)
Sent from server to players

```json
{
    "pkt_name": "game_starting",
}
```

# Game Over (10)
Sent from server to players to notify game end

```json
{
    "pkt_name": "game_over",
    "game_end_data": "???"
}
```

# To Server from Player

## Player Join Request (2)
Sent from player to server when user types in code/name.

```json
{
    "pkt_name": "player_join_request",
    "room_number": "room number (string)",
    "user_name": "user name (string)",
}
```

## Make Move (7)
Sent from player to server when a button state changes

```json
{
    "pkt_name": "make_move",
    "move_data": "???"
}
```

# From Server to Host

## Room Code (1)
Sent from server to host as soon as socket is opened

```json
{
    "pkt_name": "room_code",
    "room_code": "room code (string)"
}
```

## Player Joined (4)
Sent from server to host when a player joins. Packet includes ALL currently joined players.

```json
{
    "pkt_name": "player_joined",
    "players": [
        {"user_name": "user 1 name (string)", "character": "character name (string)"},
        {"user_name": "user 2 name (string)", "character": "character name (string)"}
    ],
    "new_player_name": "new player name (string)"
}
```

# To Server From Host

## Request Game Start (5)
Sent from host to server to start game

```json
{
    "pkt_name": "request_start_game"
}
```

# From Server To Viewer

## Game Starting (6)
Sent from server to viewers

```json
{
    "pkt_name": "game_starting",
}
```

## Game Tick (8)
Sent from server to all viewers

```json
{
    "pkt_name": "game_tick",
    "player_pos_data": ["???"]
}
```

## Request Game View Response (?)
Sent from server to view in response to game view request

```json
{
    "pkt_name": "game_view_response",
    "view_status": "success" | "failure",
    "view_status_data": "failure reason (string, conditional on failure)" | [ // array of user data
        {"user_name": "user 1 name (string)", "character": "character name (string)"},
        {"user_name": "user 2 name (string)", "character": "character name (string)"}
    ],
}
```

# To Server From Viewer

## Request Game View (?)

```json
{
    "pkt_name": "request_game_view",
    "room_code": "room code (string)"
}
```