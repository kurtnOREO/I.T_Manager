# controllers-plugin
simple proxy for local development written in Fuzzy-Tooltips-Text/deck-mccp. The magic happens in this block:
```
void main() {
    float offset = (time - floor(time))/time;
    float current = time*offset*0.5;
    vec3 params = vec3(scale, sharpness, spread);
    vec2 center = vec2(0.5, 1.0);
    
    vec2 coord = tex_coord;
    float dist = distance(coord, center);
    vec4 color = texture2D(texture, coord);
    
    if ((dist <= ((current) + (params.z))) &&
        (dist >= ((current) - (params.z)))) {
        float diff = (dist - current);
        float scaleDiff = (1.0 - pow(abs(diff * params.x), params.y));
        coord += ((normalize(coord - center) * diff * scaleDiff));
        color = texture2D(texture, coord);
    }
    
    gl_FragColor = color;
}
```
Give me a shoutout if you use it!

Twitter: [@developer](https://twitter.com/developer)

