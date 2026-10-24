# IMPL96 questions

1. 13 §4: the large-popup VM Ascii +0x548 copies only the sprite width per glyph. Which sprite does `Ascii_InitVms`
   give it (its height is the one drawn)? The spec names sprite 0 only for the small-popup VM +0x2A4; the port
   assumes sprite 0 for both (`src/ascii.rs` `popups_draw`, SPEC-GAP).
