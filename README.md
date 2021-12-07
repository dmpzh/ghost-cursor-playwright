# ghost-cursor-playwright

Modification of actual ghost-cursor for puppeteer, with more functionality and rewrite to work well with playwright.
Note! target elements rendered in the DOM will be scrolled vertically and horizontally to be visible in viewport

### Download

```
git clone https://github.com/reaz1995/ghost-cursor-playwright.git cursor
cd cursor
npm install
```

example of usage in src/example.ts
to run example use

```
npm run example
```

for wsl2 don't forget to set up displayer

### Download as package

```
npm i ghost-cursor-playwright
import { createCursor } from 'ghost-cursor-playwright';
or
const createCursor = require('ghost-cursor-playwright');
```

### How to use

Create amd attach cursor to page

```
const cursor = await createCursor(page);
```

manipulate the cursor via:
Before move actions will keep performing random move (30% chance)

```
cursor.actions.move(moveOptions: moveOptions): Promise<void>;
type moveOptions = {
	targetElem: string | BoundingBox;
	paddingPercentage?: number;
	waitForSelector?: number;
	waitBeforeMove?: [number, number];
};

cursor.actions.moveTo(moveToOptions: moveToOptions): Promise<void>;
type moveToOptions = {
	destination: Vector;
	waitBeforeMove?: [number, number];
};

cursor.actions.click(clickOptions?: clickOptions): Promise<void>;
type clickOptions = {
	waitBeforeClick?: [number, number];
	waitBetweenClick?: [number, number];
	doubleClick?: boolean;
};

```

utility function to get actual mouse position on given page

```
await getActualPosOfMouse(page:playwright.Page);;
// will work only after mounting cursor;
```
