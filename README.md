# snippets
Interesting takeaways from books too rare to keep in mind but to good to be forgotten

- Proxys can be used with a quick object literal to make an object where properties nested below non-existing properties can be created on the fly

      function Folder() { // from Secrets of the javascript ninja 2nd ed by Resig/Bibeault/Maras
        return new Proxy(
          {},
          {
            get: (target, property) => {
              if (!(property in target)) {
                target[property] = new Folder(); // create accessed property if it doesn't exist
              }
              return target[property];
            },
          }
        );
      }

- convert to number with unary +

      const b = "6";
      const a = +b;
