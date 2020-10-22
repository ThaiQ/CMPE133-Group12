## Chatbox
```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px

subgraph Create a Chatbox
    start["#cir;"]:::points
    exit["#bull;"]:::points
    start --> vr{Host's account is registered to the course?}
    vr --> |No| exit
    vr --> |Yes| cr[Create chatbox and register it to the course]
    cr --> hs[Add host to chatbox] --> exit
end

subgraph Delete a Chatbox
    start2["#cir;"]:::points
    exit2["#bull;"]:::points
    start2 --> vr2{"Account belong to host account (creator account)?"}
    vr2 --> |No| exit2
    vr2 --> |Yes| Delete --> exit2
end
```

<div style="page-break-after: always;"></div>

```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px

subgraph Reply in a Chatbox
    start3["#cir;"]:::points
    exit3["#bull;"]:::points
    start3 --> vr3{"Account is registered to the correct Chatbox?"}

    vr3 --> |No| exit3
    vr3 --> |Yes| re[Type a reply] --> send{Send?}
    send --> |No| exit3
    send --> |Yes| Send --> exit3
end

subgraph Leave a Chatbox
    start2["#cir;"]:::points
    exit2["#bull;"]:::points
    start2 --> vr2{"Account is registered to the correct Chatbox?"}
    vr2 --> |No| exit2
    vr2 --> |Yes| Leave --> exit2
end
```

<div style="page-break-after: always;"></div>

```mermaid
graph TD
classDef points fill:transparant,stroke:none,stroke-width:0px, fill-opacity:0, font-size:30px

subgraph Add a member in Chatbox
    start["#cir;"]:::points
    exit["#bull;"]:::points
    start --> vr{Account is registered to the correct Chatbox?}
    vr --> |No| exit
    vr --> |Yes| show[View all members of course]
    show --> hs{Choose a person?}
    hs --> |Yes| hss{Person registered to course?}
    hs --> |No| exit
    hss --> |No| show
    hss --> |Yes| add[Add person]
    add --> Save --> exit
end

subgraph Remove a member in Chatbox
    start2["#cir;"]:::points
    exit2["#bull;"]:::points
    start2 --> vr2{Account is registered to the correct Chatbox?}
    vr2 --> |No| exit2
    vr2 --> |Yes| show2[View all members of Chatbox]
    show2 --> hs2{Choose a person?}
    
    hs2 --> |Yes| hss2{Person is the owner?}
    hs2 --> |No| exit2

    hss2 --> |Yes| exit2
    hss2 --> |No| rem[Remove person]
    rem --> save2[Save] --> exit2
end
```