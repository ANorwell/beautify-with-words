beautify-with-words
===================

`beautify-with-words` beautifies javascript and replaces variable names with unique "long-ish words". It uses [UglifyJS2](https://github.com/mishoo/UglifyJS2)'s beautifier, but uses a phonetic word generator to rename variables. This makes it <del>easier</del> less-hard to read unminified code and do things like search-and-replace.


### Installation ###
With [`npm`](http://npmjs.org/) as a global package:

```bash
{sudo} npm install -g beautify-with-words
```

### Usage ###

```
beautify-with-words [input_file.js] [options]
```

`beautify-with-words` takes one file at a time – or, if no input file is specified, then input is read from `STDIN`.

* Use the `-o` / `--output` option to specify an output file. By default, the output goes to `STDOUT`;
* Use the `-b` / `--beautify` to pass UglifyJS2 [beautifier options](https://github.com/mishoo/UglifyJS2#beautifier-options);
* And `-h` / `--help` for help.

Reading from, and saving to, a file:

```
beautify-with-words backbone-min.js -o backbone-youre-beautiful-regardless.js
```

Send the output to `STDOUT`, and turn off syntax _beatification_ but keep variable renaming:

```
beautify-with-words backbone-min.js -b beautify=false
```

Tell the beautifier to always insert brackets in `if`, `for`, `do`, `while` or `with` statements. Go [here](https://github.com/mishoo/UglifyJS2#beautifier-options) for more options.

```
beautify-with-words backbone-min.js -b bracketize=true
```


### Sample ###

This:

```bash
curl http://cdnjs.cloudflare.com/ajax/libs/backbone.js/1.1.0/backbone-min.js | beautify-with-words
```

Turns this:

```js
// stuff...
if(!h&&typeof require!=="undefined")h=require("underscore");a.$=t.jQuery||t.Zepto||t.ender||t.$;a.noConflict=function(){t.Backbone=e;return this};a.emulateHTTP=false;a.emulateJSON=false;var o=a.Events={on:function(t,e,i){if(!l(this,"on",t,[e,i])||!e)return this;this._events||(this._events={});var r=this._events[t]||(this._events[t]=[]);r.push({callback:e,context:i,ctx:i||this});return this},once:function(t,e,i){if(!l(this,"once",t,[e,i])||!e)return this;var r=this;var s=h.once(function(){r.off(t,s);e.apply(this,arguments)});s._callback=e;return this.on(t,s,i)},
// more stuff...
```

Into this:

```js
(function() {
    var module = this;
    var decorator = module.Backbone;
    var factoryAbstract = [];
    var factory = factoryAbstract.push;
    var pattern = factoryAbstract.slice;
    var flyweightStrategy = factoryAbstract.splice;
    var moduleInterfaceFactory;
    if (typeof exports !== "undefined") {
        moduleInterfaceFactory = exports;
    } else {
        moduleInterfaceFactory = module.Backbone = {};
    }
    moduleInterfaceFactory.VERSION = "1.1.0";
    var interfaceStrategy = module._;
    if (!interfaceStrategy && typeof require !== "undefined") interfaceStrategy = require("underscore");
    moduleInterfaceFactory.$ = module.jQuery || module.Zepto || module.ender || module.$;
    moduleInterfaceFactory.noConflict = function() {
        module.Backbone = decorator;
        return this;
    };
    moduleInterfaceFactory.emulateHTTP = false;
    moduleInterfaceFactory.emulateJSON = false;
    var strategy = moduleInterfaceFactory.Events = {
        on: function(strategyFacade, strategyFactoryDecorator, interfaceFacade) {
            if (!flyweight(this, "on", strategyFacade, [ strategyFactoryDecorator, interfaceFacade ]) || !strategyFactoryDecorator) return this;
            this._events || (this._events = {});
            var strategyPattern = this._events[strategyFacade] || (this._events[strategyFacade] = []);
            strategyPattern.push({
                callback: strategyFactoryDecorator,
                context: interfaceFacade,
                ctx: interfaceFacade || this
            });
            return this;
        },
        once: function(patternPattern, strategyStrategy, factoryFactory) {
            if (!flyweight(this, "once", patternPattern, [ strategyStrategy, factoryFactory ]) || !strategyStrategy) return this;
            var interfaceFlyweight = this;
            var interfaceFactory = interfaceStrategy.once(function() {
                interfaceFlyweight.off(patternPattern, interfaceFactory);
                strategyStrategy.apply(this, arguments);
            });
            interfaceFactory._callback = strategyStrategy;
            return this.on(patternPattern, interfaceFactory, factoryFactory);
        },
        off: function(interfaceAbstract, interfaceStrategyFactory, factoryFacade) {
            var moduleFacadeFlyweight, abstractInterface, strategyFlyweightDecorator, abstractDecorator, factoryFacadeModule, decoratorDecorator, abstractFlyweight, patternFlyweightFlyweight;
            if (!this._events || !flyweight(this, "off", interfaceAbstract, [ interfaceStrategyFactory, factoryFacade ])) return this;
            if (!interfaceAbstract && !interfaceStrategyFactory && !factoryFacade) {
                this._events = {};
                return this;
            }
            abstractDecorator = interfaceAbstract ? [ interfaceAbstract ] : interfaceStrategy.keys(this._events);
            for (factoryFacadeModule = 0, decoratorDecorator = abstractDecorator.length; factoryFacadeModule < decoratorDecorator; factoryFacadeModule++) {
                interfaceAbstract = abstractDecorator[factoryFacadeModule];
                if (strategyFlyweightDecorator = this._events[interfaceAbstract]) {
                    this._events[interfaceAbstract] = moduleFacadeFlyweight = [];
                    if (interfaceStrategyFactory || factoryFacade) {
                        for (abstractFlyweight = 0, patternFlyweightFlyweight = strategyFlyweightDecorator.length; abstractFlyweight < patternFlyweightFlyweight; abstractFlyweight++) {
                            abstractInterface = strategyFlyweightDecorator[abstractFlyweight];
                            if (interfaceStrategyFactory && interfaceStrategyFactory !== abstractInterface.callback && interfaceStrategyFactory !== abstractInterface.callback._callback || factoryFacade && factoryFacade !== abstractInterface.context) {
                                moduleFacadeFlyweight.push(abstractInterface);
                            }
                        }
                    }
                    if (!moduleFacadeFlyweight.length) delete this._events[interfaceAbstract];
                }
            }
            return this;
        },
        trigger: function(patternFlyweightModule) {
            if (!this._events) return this;
            var abstractModuleFacade = pattern.call(arguments, 1);
            if (!flyweight(this, "trigger", patternFlyweightModule, abstractModuleFacade)) return this;
            var flyweightFlyweightModule = this._events[patternFlyweightModule];
            var abstractStrategy = this._events.all;
            if (flyweightFlyweightModule) decoratorAbstract(flyweightFlyweightModule, abstractModuleFacade);
            if (abstractStrategy) decoratorAbstract(abstractStrategy, arguments);
            return this;
        },
        stopListening: function(strategyAbstract, factoryFacadeStrategy, facadeDecoratorPattern) {
            var facadeFacade = this._listeningTo;
            if (!facadeFacade) return this;
            var modulePatternModule = !factoryFacadeStrategy && !facadeDecoratorPattern;
            if (!facadeDecoratorPattern && typeof factoryFacadeStrategy === "object") facadeDecoratorPattern = this;
            if (strategyAbstract) (facadeFacade = {})[strategyAbstract._listenId] = strategyAbstract;
            for (var moduleFactory in facadeFacade) {
                strategyAbstract = facadeFacade[moduleFactory];
                strategyAbstract.off(factoryFacadeStrategy, facadeDecoratorPattern, this);
                if (modulePatternModule || interfaceStrategy.isEmpty(strategyAbstract._events)) delete this._listeningTo[moduleFactory];
            }
            return this;
        }
    };
    var facade = /\s+/;
    var flyweight = function(factoryDecorator, moduleFacadePattern, patternDecoratorFacade, patternFactory) {
        if (!patternDecoratorFacade) return true;
        if (typeof patternDecoratorFacade === "object") {
            for (var factoryModule in patternDecoratorFacade) {
                factoryDecorator[moduleFacadePattern].apply(factoryDecorator, [ factoryModule, patternDecoratorFacade[factoryModule] ].concat(patternFactory));
            }
            return false;
        }
        if (facade.test(patternDecoratorFacade)) {
            var flyweightInterface = patternDecoratorFacade.split(facade);
            for (var abstractModule = 0, decoratorAbstractDecorator = flyweightInterface.length; abstractModule < decoratorAbstractDecorator; abstractModule++) {
                factoryDecorator[moduleFacadePattern].apply(factoryDecorator, [ flyweightInterface[abstractModule] ].concat(patternFactory));
            }
            return false;
        }
        return true;
    };
    var decoratorAbstract = function(moduleStrategy, moduleModuleFlyweight) {
        var moduleAbstractFlyweight, interfaceDecoratorPattern = -1, abstractInterfaceStrategy = moduleStrategy.length, interfaceFacadeFacade = moduleModuleFlyweight[0], decoratorFactory = moduleModuleFlyweight[1], interfaceDecorator = moduleModuleFlyweight[2];
        switch (moduleModuleFlyweight.length) {
          case 0:
            while (++interfaceDecoratorPattern < abstractInterfaceStrategy) (moduleAbstractFlyweight = moduleStrategy[interfaceDecoratorPattern]).callback.call(moduleAbstractFlyweight.ctx);
            return;

          case 1:
            while (++interfaceDecoratorPattern < abstractInterfaceStrategy) (moduleAbstractFlyweight = moduleStrategy[interfaceDecoratorPattern]).callback.call(moduleAbstractFlyweight.ctx, interfaceFacadeFacade);
            return;

          case 2:
            while (++interfaceDecoratorPattern < abstractInterfaceStrategy) (moduleAbstractFlyweight = moduleStrategy[interfaceDecoratorPattern]).callback.call(moduleAbstractFlyweight.ctx, interfaceFacadeFacade, decoratorFactory);
            return;

          case 3:
            while (++interfaceDecoratorPattern < abstractInterfaceStrategy) (moduleAbstractFlyweight = moduleStrategy[interfaceDecoratorPattern]).callback.call(moduleAbstractFlyweight.ctx, interfaceFacadeFacade, decoratorFactory, interfaceDecorator);
            return;

          default:
            while (++interfaceDecoratorPattern < abstractInterfaceStrategy) (moduleAbstractFlyweight = moduleStrategy[interfaceDecoratorPattern]).callback.apply(moduleAbstractFlyweight.ctx, moduleModuleFlyweight);
        }
    };
    var interfacePattern = {
        listenTo: "on",
        listenToOnce: "once"
    };
    interfaceStrategy.each(interfacePattern, function(abstractAbstract, abstractPattern) {
        strategy[abstractPattern] = function(abstractAbstractFlyweight, factoryStrategy, abstractAbstractDecorator) {
            var abstractFactoryModule = this._listeningTo || (this._listeningTo = {});
            var factoryFactoryInterface = abstractAbstractFlyweight._listenId || (abstractAbstractFlyweight._listenId = interfaceStrategy.uniqueId("l"));
            abstractFactoryModule[factoryFactoryInterface] = abstractAbstractFlyweight;
            if (!abstractAbstractDecorator && typeof factoryStrategy === "object") abstractAbstractDecorator = this;
            abstractAbstractFlyweight[abstractAbstract](factoryStrategy, abstractAbstractDecorator, this);
            return this;
        };
    });
    strategy.bind = strategy.on;
    strategy.unbind = strategy.off;
    interfaceStrategy.extend(moduleInterfaceFactory, strategy);
    var flyweightModule = moduleInterfaceFactory.Model = function(facadeFactoryDecorator, factoryInterfaceDecorator) {
        var abstractFactory = facadeFactoryDecorator || {};
        factoryInterfaceDecorator || (factoryInterfaceDecorator = {});
        this.cid = interfaceStrategy.uniqueId("c");
        this.attributes = {};
        if (factoryInterfaceDecorator.collection) this.collection = factoryInterfaceDecorator.collection;
        if (factoryInterfaceDecorator.parse) abstractFactory = this.parse(abstractFactory, factoryInterfaceDecorator) || {};
        abstractFactory = interfaceStrategy.defaults({}, abstractFactory, interfaceStrategy.result(this, "defaults"));
        this.set(abstractFactory, factoryInterfaceDecorator);
        this.changed = {};
        this.initialize.apply(this, arguments);
    };
    interfaceStrategy.extend(flyweightModule.prototype, strategy, {
        changed: null,
        validationError: null,
        idAttribute: "id",
        initialize: function() {},
        toJSON: function(patternFacade) {
            return interfaceStrategy.clone(this.attributes);
        },
        sync: function() {
            return moduleInterfaceFactory.sync.apply(this, arguments);
        },
        get: function(strategyModuleStrategy) {
            return this.attributes[strategyModuleStrategy];
        },
        escape: function(moduleModuleModule) {
            return interfaceStrategy.escape(this.get(moduleModuleModule));
        },
        has: function(moduleInterface) {
            return this.get(moduleInterface) != null;
        },
        set: function(moduleFactoryAbstract, moduleFacadeInterface, patternInterface) {
            var facadeAbstract, interfaceAbstractInterface, modulePatternFacade, facadePatternModule, patternFactoryInterface, flyweightPatternFactoryFacade, facadeFacadeFlyweight, moduleDecorator;
            if (moduleFactoryAbstract == null) return this;
            if (typeof moduleFactoryAbstract === "object") {
                interfaceAbstractInterface = moduleFactoryAbstract;
                patternInterface = moduleFacadeInterface;
            } else {
                (interfaceAbstractInterface = {})[moduleFactoryAbstract] = moduleFacadeInterface;
            }
            patternInterface || (patternInterface = {});
            if (!this._validate(interfaceAbstractInterface, patternInterface)) return false;
            modulePatternFacade = patternInterface.unset;
            patternFactoryInterface = patternInterface.silent;
            facadePatternModule = [];
            flyweightPatternFactoryFacade = this._changing;
            this._changing = true;
            if (!flyweightPatternFactoryFacade) {
                this._previousAttributes = interfaceStrategy.clone(this.attributes);
                this.changed = {};
            }
            moduleDecorator = this.attributes, facadeFacadeFlyweight = this._previousAttributes;
            if (this.idAttribute in interfaceAbstractInterface) this.id = interfaceAbstractInterface[this.idAttribute];
            for (facadeAbstract in interfaceAbstractInterface) {
                moduleFacadeInterface = interfaceAbstractInterface[facadeAbstract];
                if (!interfaceStrategy.isEqual(moduleDecorator[facadeAbstract], moduleFacadeInterface)) facadePatternModule.push(facadeAbstract);
                if (!interfaceStrategy.isEqual(facadeFacadeFlyweight[facadeAbstract], moduleFacadeInterface)) {
                    this.changed[facadeAbstract] = moduleFacadeInterface;
                } else {
                    delete this.changed[facadeAbstract];
                }
                modulePatternFacade ? delete moduleDecorator[facadeAbstract] : moduleDecorator[facadeAbstract] = moduleFacadeInterface;
            }
            if (!patternFactoryInterface) {
                if (facadePatternModule.length) this._pending = true;
                for (var interfaceStrategyFacade = 0, factoryPatternModule = facadePatternModule.length; interfaceStrategyFacade < factoryPatternModule; interfaceStrategyFacade++) {
                    this.trigger("change:" + facadePatternModule[interfaceStrategyFacade], this, moduleDecorator[facadePatternModule[interfaceStrategyFacade]], patternInterface);
                }
            }
            if (flyweightPatternFactoryFacade) return this;
            if (!patternFactoryInterface) {
                while (this._pending) {
                    this._pending = false;
                    this.trigger("change", this, patternInterface);
                }
            }
            this._pending = false;
            this._changing = false;
            return this;
        },
        unset: function(patternInterfaceModule, patternFlyweightDecoratorFacade) {
            return this.set(patternInterfaceModule, void 0, interfaceStrategy.extend({}, patternFlyweightDecoratorFacade, {
                unset: true
            }));
        },
        clear: function(strategyInterfaceStrategy) {
            var interfaceInterfaceInterface = {};
            for (var decoratorFacadeFacade in this.attributes) interfaceInterfaceInterface[decoratorFacadeFacade] = void 0;
            return this.set(interfaceInterfaceInterface, interfaceStrategy.extend({}, strategyInterfaceStrategy, {
                unset: true
            }));
        },
        hasChanged: function(flyweightFacade) {
            if (flyweightFacade == null) return !interfaceStrategy.isEmpty(this.changed);
            return interfaceStrategy.has(this.changed, flyweightFacade);
        },
        changedAttributes: function(flyweightStrategyInterface) {
            if (!flyweightStrategyInterface) return this.hasChanged() ? interfaceStrategy.clone(this.changed) : false;
            var strategyStrategyModule, moduleStrategyFlyweight = false;
            var decoratorFactoryPattern = this._changing ? this._previousAttributes : this.attributes;
            for (var decoratorFacadeInterface in flyweightStrategyInterface) {
                if (interfaceStrategy.isEqual(decoratorFactoryPattern[decoratorFacadeInterface], strategyStrategyModule = flyweightStrategyInterface[decoratorFacadeInterface])) continue;
                (moduleStrategyFlyweight || (moduleStrategyFlyweight = {}))[decoratorFacadeInterface] = strategyStrategyModule;
            }
            return moduleStrategyFlyweight;
        },
        previous: function(decoratorAbstractAbstract) {
            if (decoratorAbstractAbstract == null || !this._previousAttributes) return null;
            return this._previousAttributes[decoratorAbstractAbstract];
        },
        previousAttributes: function() {
            return interfaceStrategy.clone(this._previousAttributes);
        },
        fetch: function(moduleDecoratorStrategyFactory) {
            moduleDecoratorStrategyFactory = moduleDecoratorStrategyFactory ? interfaceStrategy.clone(moduleDecoratorStrategyFactory) : {};
            if (moduleDecoratorStrategyFactory.parse === void 0) moduleDecoratorStrategyFactory.parse = true;
            var strategyInterfaceFacade = this;
            var patternAbstractFacade = moduleDecoratorStrategyFactory.success;
            moduleDecoratorStrategyFactory.success = function(factoryStrategyModuleInterface) {
                if (!strategyInterfaceFacade.set(strategyInterfaceFacade.parse(factoryStrategyModuleInterface, moduleDecoratorStrategyFactory), moduleDecoratorStrategyFactory)) return false;
                if (patternAbstractFacade) patternAbstractFacade(strategyInterfaceFacade, factoryStrategyModuleInterface, moduleDecoratorStrategyFactory);
                strategyInterfaceFacade.trigger("sync", strategyInterfaceFacade, factoryStrategyModuleInterface, moduleDecoratorStrategyFactory);
            };
            interfaceModule(this, moduleDecoratorStrategyFactory);
            return this.sync("read", this, moduleDecoratorStrategyFactory);
        },
        save: function(decoratorFlyweightInterface, moduleInterfaceStrategy, factoryAbstractDecorator) {
            var factoryAbstractStrategy, factoryStrategyStrategy, facadeFactoryFacadePattern, abstractDecoratorFacade = this.attributes;
            if (decoratorFlyweightInterface == null || typeof decoratorFlyweightInterface === "object") {
                factoryAbstractStrategy = decoratorFlyweightInterface;
                factoryAbstractDecorator = moduleInterfaceStrategy;
            } else {
                (factoryAbstractStrategy = {})[decoratorFlyweightInterface] = moduleInterfaceStrategy;
            }
            factoryAbstractDecorator = interfaceStrategy.extend({
                validate: true
            }, factoryAbstractDecorator);
            if (factoryAbstractStrategy && !factoryAbstractDecorator.wait) {
                if (!this.set(factoryAbstractStrategy, factoryAbstractDecorator)) return false;
            } else {
                if (!this._validate(factoryAbstractStrategy, factoryAbstractDecorator)) return false;
            }
            if (factoryAbstractStrategy && factoryAbstractDecorator.wait) {
                this.attributes = interfaceStrategy.extend({}, abstractDecoratorFacade, factoryAbstractStrategy);
            }
            if (factoryAbstractDecorator.parse === void 0) factoryAbstractDecorator.parse = true;
            var abstractInterfaceFactory = this;
            var abstractAbstractAbstract = factoryAbstractDecorator.success;
            factoryAbstractDecorator.success = function(facadeFlyweightStrategy) {
                abstractInterfaceFactory.attributes = abstractDecoratorFacade;
                var flyweightDecoratorInterface = abstractInterfaceFactory.parse(facadeFlyweightStrategy, factoryAbstractDecorator);
                if (factoryAbstractDecorator.wait) flyweightDecoratorInterface = interfaceStrategy.extend(factoryAbstractStrategy || {}, flyweightDecoratorInterface);
                if (interfaceStrategy.isObject(flyweightDecoratorInterface) && !abstractInterfaceFactory.set(flyweightDecoratorInterface, factoryAbstractDecorator)) {
                    return false;
                }
                if (abstractAbstractAbstract) abstractAbstractAbstract(abstractInterfaceFactory, facadeFlyweightStrategy, factoryAbstractDecorator);
                abstractInterfaceFactory.trigger("sync", abstractInterfaceFactory, facadeFlyweightStrategy, factoryAbstractDecorator);
            };
            interfaceModule(this, factoryAbstractDecorator);
            factoryStrategyStrategy = this.isNew() ? "create" : factoryAbstractDecorator.patch ? "patch" : "update";
            if (factoryStrategyStrategy === "patch") factoryAbstractDecorator.attrs = factoryAbstractStrategy;
            facadeFactoryFacadePattern = this.sync(factoryStrategyStrategy, this, factoryAbstractDecorator);
            if (factoryAbstractStrategy && factoryAbstractDecorator.wait) this.attributes = abstractDecoratorFacade;
            return facadeFactoryFacadePattern;
        },
        destroy: function(patternInterfaceStrategy) {
            patternInterfaceStrategy = patternInterfaceStrategy ? interfaceStrategy.clone(patternInterfaceStrategy) : {};
            var flyweightAbstractStrategy = this;
            var patternModuleModule = patternInterfaceStrategy.success;
            var strategyAbstractAbstract = function() {
                flyweightAbstractStrategy.trigger("destroy", flyweightAbstractStrategy, flyweightAbstractStrategy.collection, patternInterfaceStrategy);
            };
            patternInterfaceStrategy.success = function(factoryPatternFlyweight) {
                if (patternInterfaceStrategy.wait || flyweightAbstractStrategy.isNew()) strategyAbstractAbstract();
                if (patternModuleModule) patternModuleModule(flyweightAbstractStrategy, factoryPatternFlyweight, patternInterfaceStrategy);
                if (!flyweightAbstractStrategy.isNew()) flyweightAbstractStrategy.trigger("sync", flyweightAbstractStrategy, factoryPatternFlyweight, patternInterfaceStrategy);
            };
            if (this.isNew()) {
                patternInterfaceStrategy.success();
                return false;
            }
            interfaceModule(this, patternInterfaceStrategy);
            var abstractFacadeStrategy = this.sync("delete", this, patternInterfaceStrategy);
            if (!patternInterfaceStrategy.wait) strategyAbstractAbstract();
            return abstractFacadeStrategy;
        },
        url: function() {
            var flyweightDecoratorFactory = interfaceStrategy.result(this, "urlRoot") || interfaceStrategy.result(this.collection, "url") || flyweightFactoryFactory();
            if (this.isNew()) return flyweightDecoratorFactory;
            return flyweightDecoratorFactory + (flyweightDecoratorFactory.charAt(flyweightDecoratorFactory.length - 1) === "/" ? "" : "/") + encodeURIComponent(this.id);
        },
        parse: function(patternFlyweightFacade, moduleModule) {
            return patternFlyweightFacade;
        },
        clone: function() {
            return new this.constructor(this.attributes);
        },
        isNew: function() {
            return this.id == null;
        },
        isValid: function(decoratorModule) {
            return this._validate({}, interfaceStrategy.extend(decoratorModule || {}, {
                validate: true
            }));
        },
        _validate: function(patternModuleDecorator, patternStrategy) {
            if (!patternStrategy.validate || !this.validate) return true;
            patternModuleDecorator = interfaceStrategy.extend({}, this.attributes, patternModuleDecorator);
            var decoratorStrategy = this.validationError = this.validate(patternModuleDecorator, patternStrategy) || null;
            if (!decoratorStrategy) return true;
            this.trigger("invalid", this, decoratorStrategy, interfaceStrategy.extend(patternStrategy, {
                validationError: decoratorStrategy
            }));
            return false;
        }
    });
    var flyweightPattern = [ "keys", "values", "pairs", "invert", "pick", "omit" ];
    interfaceStrategy.each(flyweightPattern, function(moduleInterfaceInterface) {
        flyweightModule.prototype[moduleInterfaceInterface] = function() {
            var patternModule = pattern.call(arguments);
            patternModule.unshift(this.attributes);
            return interfaceStrategy[moduleInterfaceInterface].apply(interfaceStrategy, patternModule);
        };
    });
    var interfaceInterface = moduleInterfaceFactory.Collection = function(moduleFlyweightFacade, decoratorStrategyFactory) {
        decoratorStrategyFactory || (decoratorStrategyFactory = {});
        if (decoratorStrategyFactory.model) this.model = decoratorStrategyFactory.model;
        if (decoratorStrategyFactory.comparator !== void 0) this.comparator = decoratorStrategyFactory.comparator;
        this._reset();
        this.initialize.apply(this, arguments);
        if (moduleFlyweightFacade) this.reset(moduleFlyweightFacade, interfaceStrategy.extend({
            silent: true
        }, decoratorStrategyFactory));
    };
    var flyweightFlyweight = {
        add: true,
        remove: true,
        merge: true
    };
    var facadeModule = {
        add: true,
        remove: false
    };
    interfaceStrategy.extend(interfaceInterface.prototype, strategy, {
        model: flyweightModule,
        initialize: function() {},
        toJSON: function(factoryFlyweight) {
            return this.map(function(interfaceModuleFlyweight) {
                return interfaceModuleFlyweight.toJSON(factoryFlyweight);
            });
        },
        sync: function() {
            return moduleInterfaceFactory.sync.apply(this, arguments);
        },
        add: function(patternFlyweightModuleInterface, strategyAbstractPattern) {
            return this.set(patternFlyweightModuleInterface, interfaceStrategy.extend({
                merge: false
            }, strategyAbstractPattern, facadeModule));
        },
        remove: function(abstractFactoryStrategy, flyweightFactoryPattern) {
            var flyweightInterfaceModule = !interfaceStrategy.isArray(abstractFactoryStrategy);
            abstractFactoryStrategy = flyweightInterfaceModule ? [ abstractFactoryStrategy ] : interfaceStrategy.clone(abstractFactoryStrategy);
            flyweightFactoryPattern || (flyweightFactoryPattern = {});
            var interfacePatternFlyweight, strategyModuleFlyweightStrategy, interfaceInterfaceStrategy, facadeInterfaceInterface;
            for (interfacePatternFlyweight = 0, strategyModuleFlyweightStrategy = abstractFactoryStrategy.length; interfacePatternFlyweight < strategyModuleFlyweightStrategy; interfacePatternFlyweight++) {
                facadeInterfaceInterface = abstractFactoryStrategy[interfacePatternFlyweight] = this.get(abstractFactoryStrategy[interfacePatternFlyweight]);
                if (!facadeInterfaceInterface) continue;
                delete this._byId[facadeInterfaceInterface.id];
                delete this._byId[facadeInterfaceInterface.cid];
                interfaceInterfaceStrategy = this.indexOf(facadeInterfaceInterface);
                this.models.splice(interfaceInterfaceStrategy, 1);
                this.length--;
                if (!flyweightFactoryPattern.silent) {
                    flyweightFactoryPattern.index = interfaceInterfaceStrategy;
                    facadeInterfaceInterface.trigger("remove", facadeInterfaceInterface, this, flyweightFactoryPattern);
                }
                this._removeReference(facadeInterfaceInterface);
            }
            return flyweightInterfaceModule ? abstractFactoryStrategy[0] : abstractFactoryStrategy;
        },
        set: function(strategyFacadeAbstract, interfaceModuleFactory) {
            interfaceModuleFactory = interfaceStrategy.defaults({}, interfaceModuleFactory, flyweightFlyweight);
            if (interfaceModuleFactory.parse) strategyFacadeAbstract = this.parse(strategyFacadeAbstract, interfaceModuleFactory);
            var patternPatternFactory = !interfaceStrategy.isArray(strategyFacadeAbstract);
            strategyFacadeAbstract = patternPatternFactory ? strategyFacadeAbstract ? [ strategyFacadeAbstract ] : [] : interfaceStrategy.clone(strategyFacadeAbstract);
            var facadePattern, facadeAbstractPattern, strategyPatternFacade, abstractDecoratorFactory, facadeStrategyFactory, patternAbstract, strategyStrategyStrategy;
            var abstractPatternDecorator = interfaceModuleFactory.at;
            var patternFlyweightInterface = this.model;
            var moduleFlyweight = this.comparator && abstractPatternDecorator == null && interfaceModuleFactory.sort !== false;
            var interfaceModuleInterface = interfaceStrategy.isString(this.comparator) ? this.comparator : null;
            var patternStrategyFactory = [], strategyModule = [], patternInterfaceFacade = {};
            var modulePatternStrategy = interfaceModuleFactory.add, abstractDecoratorPattern = interfaceModuleFactory.merge, facadeStrategyModule = interfaceModuleFactory.remove;
            var strategyPatternFactoryAbstract = !moduleFlyweight && modulePatternStrategy && facadeStrategyModule ? [] : false;
            for (facadePattern = 0, facadeAbstractPattern = strategyFacadeAbstract.length; facadePattern < facadeAbstractPattern; facadePattern++) {
                facadeStrategyFactory = strategyFacadeAbstract[facadePattern];
                if (facadeStrategyFactory instanceof flyweightModule) {
                    strategyPatternFacade = abstractDecoratorFactory = facadeStrategyFactory;
                } else {
                    strategyPatternFacade = facadeStrategyFactory[patternFlyweightInterface.prototype.idAttribute];
                }
                if (patternAbstract = this.get(strategyPatternFacade)) {
                    if (facadeStrategyModule) patternInterfaceFacade[patternAbstract.cid] = true;
                    if (abstractDecoratorPattern) {
                        facadeStrategyFactory = facadeStrategyFactory === abstractDecoratorFactory ? abstractDecoratorFactory.attributes : facadeStrategyFactory;
                        if (interfaceModuleFactory.parse) facadeStrategyFactory = patternAbstract.parse(facadeStrategyFactory, interfaceModuleFactory);
                        patternAbstract.set(facadeStrategyFactory, interfaceModuleFactory);
                        if (moduleFlyweight && !strategyStrategyStrategy && patternAbstract.hasChanged(interfaceModuleInterface)) strategyStrategyStrategy = true;
                    }
                    strategyFacadeAbstract[facadePattern] = patternAbstract;
                } else if (modulePatternStrategy) {
                    abstractDecoratorFactory = strategyFacadeAbstract[facadePattern] = this._prepareModel(facadeStrategyFactory, interfaceModuleFactory);
                    if (!abstractDecoratorFactory) continue;
                    patternStrategyFactory.push(abstractDecoratorFactory);
                    abstractDecoratorFactory.on("all", this._onModelEvent, this);
                    this._byId[abstractDecoratorFactory.cid] = abstractDecoratorFactory;
                    if (abstractDecoratorFactory.id != null) this._byId[abstractDecoratorFactory.id] = abstractDecoratorFactory;
                }
                if (strategyPatternFactoryAbstract) strategyPatternFactoryAbstract.push(patternAbstract || abstractDecoratorFactory);
            }
            if (facadeStrategyModule) {
                for (facadePattern = 0, facadeAbstractPattern = this.length; facadePattern < facadeAbstractPattern; ++facadePattern) {
                    if (!patternInterfaceFacade[(abstractDecoratorFactory = this.models[facadePattern]).cid]) strategyModule.push(abstractDecoratorFactory);
                }
                if (strategyModule.length) this.remove(strategyModule, interfaceModuleFactory);
            }
            if (patternStrategyFactory.length || strategyPatternFactoryAbstract && strategyPatternFactoryAbstract.length) {
                if (moduleFlyweight) strategyStrategyStrategy = true;
                this.length += patternStrategyFactory.length;
                if (abstractPatternDecorator != null) {
                    for (facadePattern = 0, facadeAbstractPattern = patternStrategyFactory.length; facadePattern < facadeAbstractPattern; facadePattern++) {
                        this.models.splice(abstractPatternDecorator + facadePattern, 0, patternStrategyFactory[facadePattern]);
                    }
                } else {
                    if (strategyPatternFactoryAbstract) this.models.length = 0;
                    var factoryPattern = strategyPatternFactoryAbstract || patternStrategyFactory;
                    for (facadePattern = 0, facadeAbstractPattern = factoryPattern.length; facadePattern < facadeAbstractPattern; facadePattern++) {
                        this.models.push(factoryPattern[facadePattern]);
                    }
                }
            }
            if (strategyStrategyStrategy) this.sort({
                silent: true
            });
            if (!interfaceModuleFactory.silent) {
                for (facadePattern = 0, facadeAbstractPattern = patternStrategyFactory.length; facadePattern < facadeAbstractPattern; facadePattern++) {
                    (abstractDecoratorFactory = patternStrategyFactory[facadePattern]).trigger("add", abstractDecoratorFactory, this, interfaceModuleFactory);
                }
                if (strategyStrategyStrategy || strategyPatternFactoryAbstract && strategyPatternFactoryAbstract.length) this.trigger("sort", this, interfaceModuleFactory);
            }
            return patternPatternFactory ? strategyFacadeAbstract[0] : strategyFacadeAbstract;
        },
        reset: function(facadeModuleInterface, factoryFacadePattern) {
            factoryFacadePattern || (factoryFacadePattern = {});
            for (var decoratorAbstractStrategy = 0, facadeDecoratorFactoryFacade = this.models.length; decoratorAbstractStrategy < facadeDecoratorFactoryFacade; decoratorAbstractStrategy++) {
                this._removeReference(this.models[decoratorAbstractStrategy]);
            }
            factoryFacadePattern.previousModels = this.models;
            this._reset();
            facadeModuleInterface = this.add(facadeModuleInterface, interfaceStrategy.extend({
                silent: true
            }, factoryFacadePattern));
            if (!factoryFacadePattern.silent) this.trigger("reset", this, factoryFacadePattern);
            return facadeModuleInterface;
        },
        push: function(factoryModuleDecorator, patternStrategyPattern) {
            return this.add(factoryModuleDecorator, interfaceStrategy.extend({
                at: this.length
            }, patternStrategyPattern));
        },
        pop: function(patternPatternPattern) {
            var interfaceStrategyStrategy = this.at(this.length - 1);
            this.remove(interfaceStrategyStrategy, patternPatternPattern);
            return interfaceStrategyStrategy;
        },
        unshift: function(abstractStrategyDecorator, patternFlyweight) {
            return this.add(abstractStrategyDecorator, interfaceStrategy.extend({
                at: 0
            }, patternFlyweight));
        },
        shift: function(interfaceInterfaceFactory) {
            var strategyStrategyFlyweight = this.at(0);
            this.remove(strategyStrategyFlyweight, interfaceInterfaceFactory);
            return strategyStrategyFlyweight;
        },
        slice: function() {
            return pattern.apply(this.models, arguments);
        },
        get: function(patternModuleFactory) {
            if (patternModuleFactory == null) return void 0;
            return this._byId[patternModuleFactory.id] || this._byId[patternModuleFactory.cid] || this._byId[patternModuleFactory];
        },
        at: function(interfaceModuleDecorator) {
            return this.models[interfaceModuleDecorator];
        },
        where: function(strategyFlyweightFlyweight, abstractInterfaceFlyweight) {
            if (interfaceStrategy.isEmpty(strategyFlyweightFlyweight)) return abstractInterfaceFlyweight ? void 0 : [];
            return this[abstractInterfaceFlyweight ? "find" : "filter"](function(patternInterfaceAbstract) {
                for (var flyweightFactoryInterface in strategyFlyweightFlyweight) {
                    if (strategyFlyweightFlyweight[flyweightFactoryInterface] !== patternInterfaceAbstract.get(flyweightFactoryInterface)) return false;
                }
                return true;
            });
        },
        findWhere: function(decoratorFactoryInterface) {
            return this.where(decoratorFactoryInterface, true);
        },
        sort: function(factoryFacadeFacade) {
            if (!this.comparator) throw new Error("Cannot sort a set without a comparator");
            factoryFacadeFacade || (factoryFacadeFacade = {});
            if (interfaceStrategy.isString(this.comparator) || this.comparator.length === 1) {
                this.models = this.sortBy(this.comparator, this);
            } else {
                this.models.sort(interfaceStrategy.bind(this.comparator, this));
            }
            if (!factoryFacadeFacade.silent) this.trigger("sort", this, factoryFacadeFacade);
            return this;
        },
        pluck: function(abstractInterfaceModuleFlyweight) {
            return interfaceStrategy.invoke(this.models, "get", abstractInterfaceModuleFlyweight);
        },
        fetch: function(moduleAbstractStrategy) {
            moduleAbstractStrategy = moduleAbstractStrategy ? interfaceStrategy.clone(moduleAbstractStrategy) : {};
            if (moduleAbstractStrategy.parse === void 0) moduleAbstractStrategy.parse = true;
            var flyweightModuleFlyweight = moduleAbstractStrategy.success;
            var decoratorStrategyPattern = this;
            moduleAbstractStrategy.success = function(flyweightFacadeAbstract) {
                var decoratorAbstractFactory = moduleAbstractStrategy.reset ? "reset" : "set";
                decoratorStrategyPattern[decoratorAbstractFactory](flyweightFacadeAbstract, moduleAbstractStrategy);
                if (flyweightModuleFlyweight) flyweightModuleFlyweight(decoratorStrategyPattern, flyweightFacadeAbstract, moduleAbstractStrategy);
                decoratorStrategyPattern.trigger("sync", decoratorStrategyPattern, flyweightFacadeAbstract, moduleAbstractStrategy);
            };
            interfaceModule(this, moduleAbstractStrategy);
            return this.sync("read", this, moduleAbstractStrategy);
        },
        create: function(strategyInterfaceStrategyAbstract, factoryFlyweightFactory) {
            factoryFlyweightFactory = factoryFlyweightFactory ? interfaceStrategy.clone(factoryFlyweightFactory) : {};
            if (!(strategyInterfaceStrategyAbstract = this._prepareModel(strategyInterfaceStrategyAbstract, factoryFlyweightFactory))) return false;
            if (!factoryFlyweightFactory.wait) this.add(strategyInterfaceStrategyAbstract, factoryFlyweightFactory);
            var flyweightFacadeFactoryStrategy = this;
            var decoratorDecoratorInterface = factoryFlyweightFactory.success;
            factoryFlyweightFactory.success = function(decoratorDecoratorFacade, patternFlyweightDecorator, moduleStrategyStrategy) {
                if (moduleStrategyStrategy.wait) flyweightFacadeFactoryStrategy.add(decoratorDecoratorFacade, moduleStrategyStrategy);
                if (decoratorDecoratorInterface) decoratorDecoratorInterface(decoratorDecoratorFacade, patternFlyweightDecorator, moduleStrategyStrategy);
            };
            strategyInterfaceStrategyAbstract.save(null, factoryFlyweightFactory);
            return strategyInterfaceStrategyAbstract;
        },
        parse: function(interfaceInterfaceDecorator, facadeFacadeFactory) {
            return interfaceInterfaceDecorator;
        },
        clone: function() {
            return new this.constructor(this.models);
        },
        _reset: function() {
            this.length = 0;
            this.models = [];
            this._byId = {};
        },
        _prepareModel: function(interfaceFlyweightStrategyFactory, facadeDecoratorPatternPattern) {
            if (interfaceFlyweightStrategyFactory instanceof flyweightModule) {
                if (!interfaceFlyweightStrategyFactory.collection) interfaceFlyweightStrategyFactory.collection = this;
                return interfaceFlyweightStrategyFactory;
            }
            facadeDecoratorPatternPattern = facadeDecoratorPatternPattern ? interfaceStrategy.clone(facadeDecoratorPatternPattern) : {};
            facadeDecoratorPatternPattern.collection = this;
            var strategyModuleModule = new this.model(interfaceFlyweightStrategyFactory, facadeDecoratorPatternPattern);
            if (!strategyModuleModule.validationError) return strategyModuleModule;
            this.trigger("invalid", this, strategyModuleModule.validationError, facadeDecoratorPatternPattern);
            return false;
        },
        _removeReference: function(flyweightAbstract) {
            if (this === flyweightAbstract.collection) delete flyweightAbstract.collection;
            flyweightAbstract.off("all", this._onModelEvent, this);
        },
        _onModelEvent: function(strategyInterface, decoratorFlyweight, interfaceInterfacePattern, abstractAbstractInterfaceFlyweight) {
            if ((strategyInterface === "add" || strategyInterface === "remove") && interfaceInterfacePattern !== this) return;
            if (strategyInterface === "destroy") this.remove(decoratorFlyweight, abstractAbstractInterfaceFlyweight);
            if (decoratorFlyweight && strategyInterface === "change:" + decoratorFlyweight.idAttribute) {
                delete this._byId[decoratorFlyweight.previous(decoratorFlyweight.idAttribute)];
                if (decoratorFlyweight.id != null) this._byId[decoratorFlyweight.id] = decoratorFlyweight;
            }
            this.trigger.apply(this, arguments);
        }
    });
    var factoryInterface = [ "forEach", "each", "map", "collect", "reduce", "foldl", "inject", "reduceRight", "foldr", "find", "detect", "filter", "select", "reject", "every", "all", "some", "any", "include", "contains", "invoke", "max", "min", "toArray", "size", "first", "head", "take", "initial", "rest", "tail", "drop", "last", "without", "difference", "indexOf", "shuffle", "lastIndexOf", "isEmpty", "chain" ];
    interfaceStrategy.each(factoryInterface, function(facadeFacadeFlyweightAbstract) {
        interfaceInterface.prototype[facadeFacadeFlyweightAbstract] = function() {
            var abstractPatternPatternDecorator = pattern.call(arguments);
            abstractPatternPatternDecorator.unshift(this.models);
            return interfaceStrategy[facadeFacadeFlyweightAbstract].apply(interfaceStrategy, abstractPatternPatternDecorator);
        };
    });
    var facadeFlyweight = [ "groupBy", "countBy", "sortBy" ];
    interfaceStrategy.each(facadeFlyweight, function(facadeModuleFlyweight) {
        interfaceInterface.prototype[facadeModuleFlyweight] = function(decoratorAbstractInterface, strategyFacadeFlyweight) {
            var patternDecoratorDecorator = interfaceStrategy.isFunction(decoratorAbstractInterface) ? decoratorAbstractInterface : function(moduleFlyweightStrategy) {
                return moduleFlyweightStrategy.get(decoratorAbstractInterface);
            };
            return interfaceStrategy[facadeModuleFlyweight](this.models, patternDecoratorDecorator, strategyFacadeFlyweight);
        };
    });
    var decoratorFacade = moduleInterfaceFactory.View = function(flyweightStrategyPattern) {
        this.cid = interfaceStrategy.uniqueId("view");
        flyweightStrategyPattern || (flyweightStrategyPattern = {});
        interfaceStrategy.extend(this, interfaceStrategy.pick(flyweightStrategyPattern, facadeFactory));
        this._ensureElement();
        this.initialize.apply(this, arguments);
        this.delegateEvents();
    };
    var strategyFactory = /^(\S+)\s*(.*)$/;
    var facadeFactory = [ "model", "collection", "el", "id", "attributes", "className", "tagName", "events" ];
    interfaceStrategy.extend(decoratorFacade.prototype, strategy, {
        tagName: "div",
        $: function(interfaceDecoratorFactory) {
            return this.$el.find(interfaceDecoratorFactory);
        },
        initialize: function() {},
        render: function() {
            return this;
        },
        remove: function() {
            this.$el.remove();
            this.stopListening();
            return this;
        },
        setElement: function(strategyStrategyPattern, decoratorFactoryFlyweight) {
            if (this.$el) this.undelegateEvents();
            this.$el = strategyStrategyPattern instanceof moduleInterfaceFactory.$ ? strategyStrategyPattern : moduleInterfaceFactory.$(strategyStrategyPattern);
            this.el = this.$el[0];
            if (decoratorFactoryFlyweight !== false) this.delegateEvents();
            return this;
        },
        delegateEvents: function(decoratorInterfaceStrategy) {
            if (!(decoratorInterfaceStrategy || (decoratorInterfaceStrategy = interfaceStrategy.result(this, "events")))) return this;
            this.undelegateEvents();
            for (var moduleAbstractInterface in decoratorInterfaceStrategy) {
                var factoryStrategyFactory = decoratorInterfaceStrategy[moduleAbstractInterface];
                if (!interfaceStrategy.isFunction(factoryStrategyFactory)) factoryStrategyFactory = this[decoratorInterfaceStrategy[moduleAbstractInterface]];
                if (!factoryStrategyFactory) continue;
                var strategyStrategyFacade = moduleAbstractInterface.match(strategyFactory);
                var factoryAbstractInterface = strategyStrategyFacade[1], facadeFlyweightFlyweight = strategyStrategyFacade[2];
                factoryStrategyFactory = interfaceStrategy.bind(factoryStrategyFactory, this);
                factoryAbstractInterface += ".delegateEvents" + this.cid;
                if (facadeFlyweightFlyweight === "") {
                    this.$el.on(factoryAbstractInterface, factoryStrategyFactory);
                } else {
                    this.$el.on(factoryAbstractInterface, facadeFlyweightFlyweight, factoryStrategyFactory);
                }
            }
            return this;
        },
        undelegateEvents: function() {
            this.$el.off(".delegateEvents" + this.cid);
            return this;
        },
        _ensureElement: function() {
            if (!this.el) {
                var facadeInterface = interfaceStrategy.extend({}, interfaceStrategy.result(this, "attributes"));
                if (this.id) facadeInterface.id = interfaceStrategy.result(this, "id");
                if (this.className) facadeInterface["class"] = interfaceStrategy.result(this, "className");
                var patternPatternAbstractAbstract = moduleInterfaceFactory.$("<" + interfaceStrategy.result(this, "tagName") + ">").attr(facadeInterface);
                this.setElement(patternPatternAbstractAbstract, false);
            } else {
                this.setElement(interfaceStrategy.result(this, "el"), false);
            }
        }
    });
    moduleInterfaceFactory.sync = function(facadeAbstractInterface, abstractFlyweightPattern, abstractFlyweightPatternModule) {
        var decoratorInterfacePattern = flyweightDecorator[facadeAbstractInterface];
        interfaceStrategy.defaults(abstractFlyweightPatternModule || (abstractFlyweightPatternModule = {}), {
            emulateHTTP: moduleInterfaceFactory.emulateHTTP,
            emulateJSON: moduleInterfaceFactory.emulateJSON
        });
        var factoryPatternFlyweightAbstract = {
            type: decoratorInterfacePattern,
            dataType: "json"
        };
        if (!abstractFlyweightPatternModule.url) {
            factoryPatternFlyweightAbstract.url = interfaceStrategy.result(abstractFlyweightPattern, "url") || flyweightFactoryFactory();
        }
        if (abstractFlyweightPatternModule.data == null && abstractFlyweightPattern && (facadeAbstractInterface === "create" || facadeAbstractInterface === "update" || facadeAbstractInterface === "patch")) {
            factoryPatternFlyweightAbstract.contentType = "application/json";
            factoryPatternFlyweightAbstract.data = JSON.stringify(abstractFlyweightPatternModule.attrs || abstractFlyweightPattern.toJSON(abstractFlyweightPatternModule));
        }
        if (abstractFlyweightPatternModule.emulateJSON) {
            factoryPatternFlyweightAbstract.contentType = "application/x-www-form-urlencoded";
            factoryPatternFlyweightAbstract.data = factoryPatternFlyweightAbstract.data ? {
                model: factoryPatternFlyweightAbstract.data
            } : {};
        }
        if (abstractFlyweightPatternModule.emulateHTTP && (decoratorInterfacePattern === "PUT" || decoratorInterfacePattern === "DELETE" || decoratorInterfacePattern === "PATCH")) {
            factoryPatternFlyweightAbstract.type = "POST";
            if (abstractFlyweightPatternModule.emulateJSON) factoryPatternFlyweightAbstract.data._method = decoratorInterfacePattern;
            var moduleFacadeFactory = abstractFlyweightPatternModule.beforeSend;
            abstractFlyweightPatternModule.beforeSend = function(flyweightDecoratorAbstractStrategy) {
                flyweightDecoratorAbstractStrategy.setRequestHeader("X-HTTP-Method-Override", decoratorInterfacePattern);
                if (moduleFacadeFactory) return moduleFacadeFactory.apply(this, arguments);
            };
        }
        if (factoryPatternFlyweightAbstract.type !== "GET" && !abstractFlyweightPatternModule.emulateJSON) {
            factoryPatternFlyweightAbstract.processData = false;
        }
        if (factoryPatternFlyweightAbstract.type === "PATCH" && decoratorPattern) {
            factoryPatternFlyweightAbstract.xhr = function() {
                return new ActiveXObject("Microsoft.XMLHTTP");
            };
        }
        var interfaceAbstractPattern = abstractFlyweightPatternModule.xhr = moduleInterfaceFactory.ajax(interfaceStrategy.extend(factoryPatternFlyweightAbstract, abstractFlyweightPatternModule));
        abstractFlyweightPattern.trigger("request", abstractFlyweightPattern, interfaceAbstractPattern, abstractFlyweightPatternModule);
        return interfaceAbstractPattern;
    };
    var decoratorPattern = typeof window !== "undefined" && !!window.ActiveXObject && !(window.XMLHttpRequest && new XMLHttpRequest().dispatchEvent);
    var flyweightDecorator = {
        create: "POST",
        update: "PUT",
        patch: "PATCH",
        "delete": "DELETE",
        read: "GET"
    };
    moduleInterfaceFactory.ajax = function() {
        return moduleInterfaceFactory.$.ajax.apply(moduleInterfaceFactory.$, arguments);
    };
    var moduleAbstract = moduleInterfaceFactory.Router = function(strategyInterfaceAbstract) {
        strategyInterfaceAbstract || (strategyInterfaceAbstract = {});
        if (strategyInterfaceAbstract.routes) this.routes = strategyInterfaceAbstract.routes;
        this._bindRoutes();
        this.initialize.apply(this, arguments);
    };
    var strategyDecorator = /\((.*?)\)/g;
    var strategyFlyweight = /(\(\?)?:\w+/g;
    var facadeDecorator = /\*\w+/g;
    var abstractAbstractModule = /[\-{}\[\]+?.,\\\^$|#\s]/g;
    interfaceStrategy.extend(moduleAbstract.prototype, strategy, {
        initialize: function() {},
        route: function(flyweightDecoratorDecorator, abstractStrategyFacade, strategyPatternFlyweightFactory) {
            if (!interfaceStrategy.isRegExp(flyweightDecoratorDecorator)) flyweightDecoratorDecorator = this._routeToRegExp(flyweightDecoratorDecorator);
            if (interfaceStrategy.isFunction(abstractStrategyFacade)) {
                strategyPatternFlyweightFactory = abstractStrategyFacade;
                abstractStrategyFacade = "";
            }
            if (!strategyPatternFlyweightFactory) strategyPatternFlyweightFactory = this[abstractStrategyFacade];
            var strategyAbstractFactory = this;
            moduleInterfaceFactory.history.route(flyweightDecoratorDecorator, function(decoratorFactoryStrategy) {
                var facadePatternFactory = strategyAbstractFactory._extractParameters(flyweightDecoratorDecorator, decoratorFactoryStrategy);
                strategyPatternFlyweightFactory && strategyPatternFlyweightFactory.apply(strategyAbstractFactory, facadePatternFactory);
                strategyAbstractFactory.trigger.apply(strategyAbstractFactory, [ "route:" + abstractStrategyFacade ].concat(facadePatternFactory));
                strategyAbstractFactory.trigger("route", abstractStrategyFacade, facadePatternFactory);
                moduleInterfaceFactory.history.trigger("route", strategyAbstractFactory, abstractStrategyFacade, facadePatternFactory);
            });
            return this;
        },
        navigate: function(decoratorInterfaceInterface, decoratorInterfaceFlyweight) {
            moduleInterfaceFactory.history.navigate(decoratorInterfaceInterface, decoratorInterfaceFlyweight);
            return this;
        },
        _bindRoutes: function() {
            if (!this.routes) return;
            this.routes = interfaceStrategy.result(this, "routes");
            var modulePatternFactory, interfaceStrategyModule = interfaceStrategy.keys(this.routes);
            while ((modulePatternFactory = interfaceStrategyModule.pop()) != null) {
                this.route(modulePatternFactory, this.routes[modulePatternFactory]);
            }
        },
        _routeToRegExp: function(abstractFactoryFactory) {
            abstractFactoryFactory = abstractFactoryFactory.replace(abstractAbstractModule, "\\$&").replace(strategyDecorator, "(?:$1)?").replace(strategyFlyweight, function(moduleFacadeModule, moduleAbstractDecorator) {
                return moduleAbstractDecorator ? moduleFacadeModule : "([^/]+)";
            }).replace(facadeDecorator, "(.*?)");
            return new RegExp("^" + abstractFactoryFactory + "$");
        },
        _extractParameters: function(decoratorModuleInterface, flyweightFlyweightInterface) {
            var decoratorFlyweightFactory = decoratorModuleInterface.exec(flyweightFlyweightInterface).slice(1);
            return interfaceStrategy.map(decoratorFlyweightFactory, function(facadeDecoratorModule) {
                return facadeDecoratorModule ? decodeURIComponent(facadeDecoratorModule) : null;
            });
        }
    });
    var decoratorInterface = moduleInterfaceFactory.History = function() {
        this.handlers = [];
        interfaceStrategy.bindAll(this, "checkUrl");
        if (typeof window !== "undefined") {
            this.location = window.location;
            this.history = window.history;
        }
    };
    var moduleFacade = /^[#\/]|\s+$/g;
    var patternDecorator = /^\/+|\/+$/g;
    var abstractFacade = /msie [\w.]+/;
    var modulePattern = /\/$/;
    var factoryFactoryModule = /[?#].*$/;
    decoratorInterface.started = false;
    interfaceStrategy.extend(decoratorInterface.prototype, strategy, {
        interval: 50,
        getHash: function(patternPatternStrategy) {
            var patternFacadeInterface = (patternPatternStrategy || this).location.href.match(/#(.*)$/);
            return patternFacadeInterface ? patternFacadeInterface[1] : "";
        },
        getFragment: function(modulePatternFlyweight, abstractPatternFactory) {
            if (modulePatternFlyweight == null) {
                if (this._hasPushState || !this._wantsHashChange || abstractPatternFactory) {
                    modulePatternFlyweight = this.location.pathname;
                    var decoratorPatternStrategy = this.root.replace(modulePattern, "");
                    if (!modulePatternFlyweight.indexOf(decoratorPatternStrategy)) modulePatternFlyweight = modulePatternFlyweight.slice(decoratorPatternStrategy.length);
                } else {
                    modulePatternFlyweight = this.getHash();
                }
            }
            return modulePatternFlyweight.replace(moduleFacade, "");
        },
        start: function(flyweightDecoratorPatternAbstract) {
            if (decoratorInterface.started) throw new Error("Backbone.history has already been started");
            decoratorInterface.started = true;
            this.options = interfaceStrategy.extend({
                root: "/"
            }, this.options, flyweightDecoratorPatternAbstract);
            this.root = this.options.root;
            this._wantsHashChange = this.options.hashChange !== false;
            this._wantsPushState = !!this.options.pushState;
            this._hasPushState = !!(this.options.pushState && this.history && this.history.pushState);
            var decoratorFlyweightFlyweight = this.getFragment();
            var strategyFactoryStrategy = document.documentMode;
            var decoratorInterfaceModule = abstractFacade.exec(navigator.userAgent.toLowerCase()) && (!strategyFactoryStrategy || strategyFactoryStrategy <= 7);
            this.root = ("/" + this.root + "/").replace(patternDecorator, "/");
            if (decoratorInterfaceModule && this._wantsHashChange) {
                this.iframe = moduleInterfaceFactory.$('<iframe src="javascript:0" tabindex="-1" />').hide().appendTo("body")[0].contentWindow;
                this.navigate(decoratorFlyweightFlyweight);
            }
            if (this._hasPushState) {
                moduleInterfaceFactory.$(window).on("popstate", this.checkUrl);
            } else if (this._wantsHashChange && "onhashchange" in window && !decoratorInterfaceModule) {
                moduleInterfaceFactory.$(window).on("hashchange", this.checkUrl);
            } else if (this._wantsHashChange) {
                this._checkUrlInterval = setInterval(this.checkUrl, this.interval);
            }
            this.fragment = decoratorFlyweightFlyweight;
            var decoratorFacadeFactory = this.location;
            var flyweightFacadeFactory = decoratorFacadeFactory.pathname.replace(/[^\/]$/, "$&/") === this.root;
            if (this._wantsHashChange && this._wantsPushState) {
                if (!this._hasPushState && !flyweightFacadeFactory) {
                    this.fragment = this.getFragment(null, true);
                    this.location.replace(this.root + this.location.search + "#" + this.fragment);
                    return true;
                } else if (this._hasPushState && flyweightFacadeFactory && decoratorFacadeFactory.hash) {
                    this.fragment = this.getHash().replace(moduleFacade, "");
                    this.history.replaceState({}, document.title, this.root + this.fragment + decoratorFacadeFactory.search);
                }
            }
            if (!this.options.silent) return this.loadUrl();
        },
        stop: function() {
            moduleInterfaceFactory.$(window).off("popstate", this.checkUrl).off("hashchange", this.checkUrl);
            clearInterval(this._checkUrlInterval);
            decoratorInterface.started = false;
        },
        route: function(factoryStrategyFactoryModule, facadeFacadeDecorator) {
            this.handlers.unshift({
                route: factoryStrategyFactoryModule,
                callback: facadeFacadeDecorator
            });
        },
        checkUrl: function(interfaceFacadeStrategy) {
            var patternModuleFlyweightDecorator = this.getFragment();
            if (patternModuleFlyweightDecorator === this.fragment && this.iframe) {
                patternModuleFlyweightDecorator = this.getFragment(this.getHash(this.iframe));
            }
            if (patternModuleFlyweightDecorator === this.fragment) return false;
            if (this.iframe) this.navigate(patternModuleFlyweightDecorator);
            this.loadUrl();
        },
        loadUrl: function(abstractStrategyFlyweight) {
            abstractStrategyFlyweight = this.fragment = this.getFragment(abstractStrategyFlyweight);
            return interfaceStrategy.any(this.handlers, function(abstractFacadeModule) {
                if (abstractFacadeModule.route.test(abstractStrategyFlyweight)) {
                    abstractFacadeModule.callback(abstractStrategyFlyweight);
                    return true;
                }
            });
        },
        navigate: function(factoryModuleDecoratorDecorator, interfacePatternPattern) {
            if (!decoratorInterface.started) return false;
            if (!interfacePatternPattern || interfacePatternPattern === true) interfacePatternPattern = {
                trigger: !!interfacePatternPattern
            };
            var factoryFlyweightFacadeStrategy = this.root + (factoryModuleDecoratorDecorator = this.getFragment(factoryModuleDecoratorDecorator || ""));
            factoryModuleDecoratorDecorator = factoryModuleDecoratorDecorator.replace(factoryFactoryModule, "");
            if (this.fragment === factoryModuleDecoratorDecorator) return;
            this.fragment = factoryModuleDecoratorDecorator;
            if (factoryModuleDecoratorDecorator === "" && factoryFlyweightFacadeStrategy !== "/") factoryFlyweightFacadeStrategy = factoryFlyweightFacadeStrategy.slice(0, -1);
            if (this._hasPushState) {
                this.history[interfacePatternPattern.replace ? "replaceState" : "pushState"]({}, document.title, factoryFlyweightFacadeStrategy);
            } else if (this._wantsHashChange) {
                this._updateHash(this.location, factoryModuleDecoratorDecorator, interfacePatternPattern.replace);
                if (this.iframe && factoryModuleDecoratorDecorator !== this.getFragment(this.getHash(this.iframe))) {
                    if (!interfacePatternPattern.replace) this.iframe.document.open().close();
                    this._updateHash(this.iframe.location, factoryModuleDecoratorDecorator, interfacePatternPattern.replace);
                }
            } else {
                return this.location.assign(factoryFlyweightFacadeStrategy);
            }
            if (interfacePatternPattern.trigger) return this.loadUrl(factoryModuleDecoratorDecorator);
        },
        _updateHash: function(abstractModuleStrategy, moduleFacadeDecorator, flyweightPatternFactory) {
            if (flyweightPatternFactory) {
                var abstractStrategyInterface = abstractModuleStrategy.href.replace(/(javascript:|#).*$/, "");
                abstractModuleStrategy.replace(abstractStrategyInterface + "#" + moduleFacadeDecorator);
            } else {
                abstractModuleStrategy.hash = "#" + moduleFacadeDecorator;
            }
        }
    });
    moduleInterfaceFactory.history = new decoratorInterface();
    var flyweightModuleInterface = function(decoratorStrategyStrategyPattern, factoryDecoratorFactory) {
        var factoryPatternInterface = this;
        var strategyFacadeFlyweightFlyweight;
        if (decoratorStrategyStrategyPattern && interfaceStrategy.has(decoratorStrategyStrategyPattern, "constructor")) {
            strategyFacadeFlyweightFlyweight = decoratorStrategyStrategyPattern.constructor;
        } else {
            strategyFacadeFlyweightFlyweight = function() {
                return factoryPatternInterface.apply(this, arguments);
            };
        }
        interfaceStrategy.extend(strategyFacadeFlyweightFlyweight, factoryPatternInterface, factoryDecoratorFactory);
        var decoratorModuleStrategy = function() {
            this.constructor = strategyFacadeFlyweightFlyweight;
        };
        decoratorModuleStrategy.prototype = factoryPatternInterface.prototype;
        strategyFacadeFlyweightFlyweight.prototype = new decoratorModuleStrategy();
        if (decoratorStrategyStrategyPattern) interfaceStrategy.extend(strategyFacadeFlyweightFlyweight.prototype, decoratorStrategyStrategyPattern);
        strategyFacadeFlyweightFlyweight.__super__ = factoryPatternInterface.prototype;
        return strategyFacadeFlyweightFlyweight;
    };
    flyweightModule.extend = interfaceInterface.extend = moduleAbstract.extend = decoratorFacade.extend = decoratorInterface.extend = flyweightModuleInterface;
    var flyweightFactoryFactory = function() {
        throw new Error('A "url" property or function must be specified');
    };
    var interfaceModule = function(decoratorAbstractModuleModule, factoryFlyweightFactoryFactory) {
        var facadeDecoratorStrategy = factoryFlyweightFactoryFactory.error;
        factoryFlyweightFactoryFactory.error = function(abstractPatternStrategy) {
            if (facadeDecoratorStrategy) facadeDecoratorStrategy(decoratorAbstractModuleModule, abstractPatternStrategy, factoryFlyweightFactoryFactory);
            decoratorAbstractModuleModule.trigger("error", decoratorAbstractModuleModule, abstractPatternStrategy, factoryFlyweightFactoryFactory);
        };
    };
}).call(this);
```
