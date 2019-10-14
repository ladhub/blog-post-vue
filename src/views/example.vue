=================Vue javascript style=================

export default {
    name: 'asdfasdf',
    
    DONE = data: () => {
        return {
            counter: 1o,
            increment: 1,
        };
    }

    created: () => {
        console.log('This component is created');
    },
    methods: {
        'increment': (count) => { return count + this.increment },
    },
    computed: {
        'display': () => {return this.counter + 'is counter'}
    },
    props: ['count']
};

=================Vue typescript style=================

import {Vue, Component, Prop} from 'vue-property-decorator'

@Component({
    name: 'asdfsdf',
})
export default class CountComponent extends Vue {
    private counter: number = 10;
    private increment: number = 1;
    private errors: any[];
    
    @Prop({type: Number, default: 12}) private count: number;

    private created(): void {
        console.log();
    }

    private increment(): number {
        return count + this.increment;
    }

    private get display(): string {
        return this.counter + "asdf";
    }
}


built in data types:
    string[]
    number
    boolean
    {[proposalid: string]: number}
    any
    Date | string | number

const data: Date|string|number = '';

custom data types:
interface IAnything {
    field: string;
    data?: number;
}
const data: IAnything = {field: ''};

class Anything {
    field: string;
    data?: number;

    constructor() {
        field = 'field 1';
        data = 10;
    }
}
const data: Anything = new Anything();

enum RiskType {
    ULIP = 'ulip',
    Guaranteed = 1,
}
const data: RiskType = RiskType.ULIP; // ulip
const data: RiskType = RiskType.Guaranteed; // 1
const data: {[key: RiskType]: string} = {'ulip': 'ulip is best'};

inheritance:
class A {
    
}
class B extends A {
    
}

composition:
class A {
    
}
class B {
    data: A;
}

overriding:
class A {
    public print(): void {
        console.log('This is class A');
    }
}
class B extends A {
    public print(): void {
        console.log('This is class B');
    }
    public sample(): void {
        console.log('sample function from class B');
    }    
}
class C extends A {
    public print(): void {
        console.log('This is class C');
    }
    public sample(): void {
        console.log('sample function from class C');
    }    
}
const data: A = new A();
data.print(); // 'This is class A'
const data: A = new B();
data.print(); // 'This is class B'
const data: A = new C();
data.print(); // 'This is class C'
const data: B = new B();
data.print(); // 'This is class B'
data.sample(); // 'sample function from class B'

overloading:
class A {
    public print(): void {
        console.log('This is print function with no parameters');
    }
    public print(name: string): void {
        console.log('This is print function with name: ', name);
    }
}
const data: A = new A();
data.print(); // 'This is print function with no parameters'
data.print('Sumit'); // 'This is print function with name: Sumit'