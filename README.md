Nevertheless you can write your own function that traverses the tree, but that will be quite slow compared to getElementById because you cannot make use of any index:

function getElementByAttribute(attr, value, root) {
    root = root || document.body;
    if(root.hasAttribute(attr) && root.getAttribute(attr) == value) {
        return root;
    }
    var children = root.children, 
        element;
    for(var i = children.length; i--; ) {
        element = getElementByAttribute(attr, value, children[i]);
        if(element) {
            return element;
        }
    }
    return null;
}
In the worst case, this will traverse the whole tree. Think about how to change your concept so that you can make use browser functions as much as possible.

In newer browsers you use of the querySelector method, where it would just be:

var element = document.querySelector('[tokenid="14"]');
This will be much faster too.

