# ABTest

## What is ABTest?

We actually don't have any reasonable background when we design a new webstie first.  
Imagine you are making a new website, and you have two desgin choices, A and B.  
In this situation, to make sure which design is more profitable or superior, you can use ABTest.  
<br/> 
Every users will randomly access to website design A or B, even the route is same.   
You will log each case, then you can get some meaningful informations.  
By analyzing these stuffs, you can choose better design between A and B.
<br/>  
## Applied Flask Methods

### Blueprint

- **In main file**

``` python

from flask import Flask
from Mydir import Mysrc

app = Flask(__name__)
app.register_blueprint(Mysrc.BlueprintObject, url_prefix='/blog')

```

- `url_prefix` must have default route
  - so it becomes as "URL/default route/routing route"

<br/>  

- **In src**

``` python

from flask import Blueprint

BlueprintObject = Blueprint('blog', __name__) 

@BlueprintObject.route('/blog1')
def blog():
    return 'TEST BLUEPRINT'

```

### flask_login
