# Instructions

- Following Playwright test failed.
- Explain why, be concise, respect Playwright best practices.
- Provide a snippet of code with the fix, if possible.

# Test info

- Name: ui/admin.spec.ts >> Admin dashboard >> Verify that as an admin, I can see the clinic form and patient table
- Location: tests/ui/admin.spec.ts:29:3

# Error details

```
Test timeout of 30000ms exceeded while running "beforeEach" hook.
```

```
Error: page.goto: Test timeout of 30000ms exceeded.
Call log:
  - navigating to "http://127.0.0.1:4173/admin/", waiting until "load"

```

# Page snapshot

```yaml
- generic [ref=e2]:
  - complementary "Admin navigation" [ref=e3]:
    - link "Bright Smile Dental Clinic" [ref=e5] [cursor=pointer]:
      - /url: ../index.html
      - text: Bright Smile
      - emphasis [ref=e6]: Dental Clinic
    - navigation "Admin sections" [ref=e7]:
      - tablist [ref=e8]:
        - listitem [ref=e9]:
          - tab "Clinic Information" [selected] [ref=e10] [cursor=pointer]:
            - generic [ref=e12]: 
            - generic [ref=e13]: Clinic Information
        - listitem [ref=e14]:
          - tab "Patients" [ref=e15] [cursor=pointer]:
            - generic [ref=e17]: 
            - generic [ref=e18]: Patients
        - listitem [ref=e19]:
          - tab "Doctors" [ref=e20] [cursor=pointer]:
            - generic [ref=e22]: 
            - generic [ref=e23]: Doctors
    - button "Logout" [ref=e25] [cursor=pointer]:
      - generic [ref=e27]: 
      - generic [ref=e28]: Logout
  - generic [ref=e29]:
    - banner [ref=e30]:
      - text: 
      - generic [ref=e31]:
        - heading "Clinic Information" [level=1] [ref=e32]
        - paragraph [ref=e33]
    - main [ref=e35]:
      - article [ref=e36]:
        - generic [ref=e37]:
          - tabpanel [ref=e38]:
            - generic [ref=e41]:
              - paragraph [ref=e42]: Changes appear on the public homepage immediately.
              - generic [ref=e43]:
                - generic [ref=e44]: Clinic Name
                - textbox "Clinic Name" [ref=e45]
                - generic [ref=e46]: Tagline
                - textbox "Tagline" [ref=e47]
                - generic [ref=e48]: Address
                - textbox "Address" [ref=e49]
                - generic [ref=e50]:
                  - generic [ref=e51]:
                    - generic [ref=e52]: Phone
                    - textbox "Phone" [ref=e53]
                  - generic [ref=e54]:
                    - generic [ref=e55]: Email
                    - textbox "Email" [ref=e56]
                - generic [ref=e57]: Office Hours
                - textbox "Office Hours" [ref=e58]
                - list [ref=e59]:
                  - listitem [ref=e60]:
                    - button "Save Clinic Info" [ref=e61] [cursor=pointer]
          - text:  First  Previous  Next  Last
```

# Test source

```ts
  1  | import type { Page } from '@playwright/test';
  2  | 
  3  | /** Shared base for page objects: holds the Playwright {@link Page} and navigation helper. */
  4  | export abstract class BasePage {
  5  |   /**
  6  |    * @param page - Playwright page for this page object.
  7  |    */
  8  |   constructor(protected readonly page: Page) {}
  9  | 
  10 |   /**
  11 |    * Navigates to a path relative to the Playwright `baseURL`.
  12 |    * @param path - App path such as `/login.html` or `/admin/`.
  13 |    */
  14 |   async goto(path: string): Promise<void> {
> 15 |     await this.page.goto(path);
     |                     ^ Error: page.goto: Test timeout of 30000ms exceeded.
  16 |   }
  17 | }
  18 | 
```