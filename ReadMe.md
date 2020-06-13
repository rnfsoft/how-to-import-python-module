## How to import python modules in windows

#### Project structure

```
project 
    -- test 
        +-- sub1 
            -- __init__.py 
            -- d.py 
            -- e.py
            -- e_f.py
            -- context.py 
        +-- sub2 
            -- __init__.py 
            -- f.py 
            -- g.py
            -- g_h.py
            -- g_i.py
            -- context.py 
        -- __init__.py
        -- b.py 
        -- c.py
        -- h.py
        -- h_i.py
        -- context.py 
    -- a.py
    -- i.py

```

#### order: a->b->c->d->e->f->g->h->i

need sys.path to __init__.py

    import os
    import sys
    if os.path.abspath(os.path.dirname(__file__)) not in sys.path:
        sys.path.append(os.path.abspath(os.path.dirname(__file__)))

#### order: e->f

need context (parent path) to access to sibling folder

#### order: g->h

need context (parent path) to access to sibling folder

#### order: g->i

need context (parent of parent path) to access to sibling folder

#### order: h->i

need context (parent path) to access to sibling folder


#### Summary

<ul>
<li>
Need parent path to access to silbing or parent files
</li>
<li>
Need parent of parent path to access to files in the root folder (parent of parent folder is top label in this example)
</li>
<li>
Add current path to __init__.py to prevent an error of importing silbing files when called from other files eg) a->b->c

    i mport c

    ModuleNotFoundError: No module named 'c'
</li>
</ul>

#### References

https://docs.python-guide.org/writing/structure/


https://brownbears.tistory.com/296