<!-- BEGIN:nextjs-agent-rules -->
# This is NOT the Next.js you know

This version has breaking changes — APIs, conventions, and file structure may all differ from your training data. Read the relevant guide in `node_modules/next/dist/docs/` before writing any code. Heed deprecation notices.
<!-- END:nextjs-agent-rules -->

<!-- BEGIN:fmcg-distributor-agent-rules -->
# Project Context

## Intro
Our customer is a Vietnamese FMCG (Fast-moving Consumer Goods) distributor that:
- Imports goods from foreign markets like Japan, US,...
- Resells them to Vietnamese retailers like WinMart, Bach Hoa Xanh, Circle K,...

In other words, retailers place Product Orders (POs) from us.

We also have to keep track of accounting and tax compliance. We did think of Oracle or SAP, but since we are a mid-sized business, purchasing them is out of question.

## Problem
- Completing those POs on time, and can suffer from penalities if they arrive 2-3 days late.
- Keeping track of inventory (e.g. sell-in, sell-out) is time-consuming
- Resolve invoice mismatches before the end of the day, as they can't be rolled over (moved to next day).

# Folder structure

```
frontend/
├── public/                   # Static assets
└── src/                      # Source folder
    ├── app/                  # App Router files & UI composition
    │   ├── (auth)/           # Route Group: Logical sorting
    │   ├── dashboard/        # Public routes
    │   │   └── _components/  # Private: Route-specific UI
    │   └── page.tsx          # Homepage
    ├── shared-components/    # GLOBAL shared UI (e.g., buttons)    
    │   └── buttons.tsx/      # Feature components
    ├── infrastructure/       # Third-party configurations
    │   └── redux/            # Redux-related components (selectors, slices)
    │   │   └── homepageSlice # Redux slice with selectors and reducers  
    │   │   └── homepageThunk # Listens to dispatches and perform API calls
    │   └── services/         # API fetch code snippets
    ├── models/               # Business object definitions
    │   └── buttons.tsx/      # Business object
    ├── hooks/                # Global custom hooks
    └── utils/                # Global utility functions
```


# Coding conventions

## Redux Reducer notes
- Since we are going for the Redux Thunk pattern, creating extraReducers per slice is a must. 3 of these should be included: 
  - **Pending**: Setting isLoading State variable within the slice to true
  - **Fulfilled**: Set isLoading to false, the response to the variable name in the slice, based on the user's prompt.
  - **Rejected**: Set isLoading to false, and the error to the error object within the slice.

## Component composition

- When to put a new component shared-components folder: 
    + When the component can't be broken down even further (break it down further won't make it complete)
    + Common examples: Button, TextInput, Spinner, ImageUploader, Table,...

- When the user prompts a specific UI structure, in top down approach, build the UI from the bottom-up approach for ease. For example:
    - **Prompt**: On the home page, I want to create a dashboard consisting of:
        - Critical Information month's invoices, mismatches, pos-pending review, expiring today. 
        - Each item is a KpiCard, having a subtitle at the top, the number right underneath, and the unit on the right side of the number, if applicable.
    - **Execution**: Copy that, I will start from the bottom with the KpiCard, then construct the Dashboard using a Grid of KpiCards,...

## Function definition

- A function should be between 30 and 80 lines long. Anything longer should be broken down into smaller functions.
<!-- END:fmcg-distributor-agent-rules -->