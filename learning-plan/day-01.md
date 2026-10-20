# Day 01 — First request

[Plan](../learning-plan.md) · [Business stories](../USER_STORIES.MD) · [Next day](day-02.md)

**Goal:** Understand the starter app before changing it.

- [ ] Learn: an HTTP request asks the server for something; a response is what the server sends back. A controller receives a route, a service supplies its behavior, and a module connects them using dependency injection.
- [ ] Open `src/main.ts`, `src/app.module.ts`, `src/app.controller.ts`, `src/app.service.ts`, and `src/app.controller.spec.ts`. Explain `@Module`, `@Controller`, `@Get`, `@Injectable`, and why the controller receives a service in its constructor.
- [ ] Predict what `GET /` returns, then run the existing test and try the endpoint. Draw request → controller → service → response. There is no guard, validation pipe, or database in this route yet.

**Done when:** You can point to the line responsible for the returned text and explain each of the four app files without reading a script.
