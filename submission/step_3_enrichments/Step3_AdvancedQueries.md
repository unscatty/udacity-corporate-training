# Step 3 Enrichments advanced queries

### Query 1

**Description**: *Search for "Claudia" (instructor), get facets for `level`, `role`, `source` and `instructor` and also get the result count*

**Query string**: `search=Claudia&facet=level&facet=role&facet=source&facet=instructor&$count=true`

**Index**: courses

**Results**:
```json
{
  "@odata.context": "https://corporate-training-search.search.windows.net/indexes('courses-index')/$metadata#docs(*)",
  "@odata.count": 3,
  "@search.facets": {
    "source": [
      {
        "count": 3,
        "value": "Company Moodle"
      }
    ],
    "level": [
      {
        "count": 2,
        "value": "intermediate"
      },
      {
        "count": 1,
        "value": "beginner"
      }
    ],
    "instructor": [
      {
        "count": 3,
        "value": "Claudia Blackman"
      }
    ],
    "role": [
      {
        "count": 2,
        "value": "developer"
      },
      {
        "count": 1,
        "value": "admin"
      }
    ]
  },
  "value": [
    {
      "@search.score": 1.3057226,
      "Key": "company-moodle578a3319-aa7c-4d2f-b6a4-39e9638b0a85",
      "description": "For administrators, this course will teach you how our CI/CD pipelines work from an operations perspective",
      "duration": 5,
      "instructor": "Claudia Blackman",
      "level": "intermediate",
      "product": "jenkins",
      "rating_average": 4.9,
      "rating_count": 56,
      "role": "admin",
      "source": "Company Moodle",
      "title": "DevOps for Ops",
      "url": "https://www.example.com/course5",
      "keyphrases": [
        "CI/CD pipelines",
        "operations perspective",
        "administrators",
        "course"
      ],
      "instructor_profiles": [
        {
          "name": "Claudia Blackman",
          "description": "Claudia is our senior DevOps engineer. She is charged with overseeing our DevOps operations and has been with the company for 2 years. Claudia enjoys downhill skiing and is a member of the local Search & Rescue Team."
        }
      ]
    },
    {
      "@search.score": 1.3057226,
      "Key": "company-moodle9700e1dc-b293-4306-9e1b-0d345863db54",
      "description": "This course will teach you the specific ways our company uses Git. You will learn details for comments, branching, pull requests, and other procsses",
      "duration": 3,
      "instructor": "Claudia Blackman",
      "level": "beginner",
      "product": "git",
      "rating_average": 4.5,
      "rating_count": 125,
      "role": "developer",
      "source": "Company Moodle",
      "title": "Git Workflow ",
      "url": "https://www.example.com/course3",
      "keyphrases": [
        "specific ways",
        "other procsses",
        "course",
        "company",
        "Git",
        "details",
        "comments",
        "requests"
      ],
      "instructor_profiles": [
        {
          "name": "Claudia Blackman",
          "description": "Claudia is our senior DevOps engineer. She is charged with overseeing our DevOps operations and has been with the company for 2 years. Claudia enjoys downhill skiing and is a member of the local Search & Rescue Team."
        }
      ]
    },
    {
      "@search.score": 1.3057226,
      "Key": "company-moodleb51ede14-025f-49ad-9e9e-44ad284eedda",
      "description": "For developers, this course will teach you how to hook your dev work into our existing CI/CD pipelines.",
      "duration": 3,
      "instructor": "Claudia Blackman",
      "level": "intermediate",
      "product": "jenkins",
      "rating_average": 3.8,
      "rating_count": 101,
      "role": "developer",
      "source": "Company Moodle",
      "title": "DevOps for Dev",
      "url": "https://www.example.com/course4",
      "keyphrases": [
        "existing CI/CD pipelines",
        "dev work",
        "developers",
        "course"
      ],
      "instructor_profiles": [
        {
          "name": "Claudia Blackman",
          "description": "Claudia is our senior DevOps engineer. She is charged with overseeing our DevOps operations and has been with the company for 2 years. Claudia enjoys downhill skiing and is a member of the local Search & Rescue Team."
        }
      ]
    }
  ]
}
```

---

### Query 2

**Description**: *Search for "azure devops artificial intelligence", where `rating_average` is greater than or equal to 4.75 and `level` is either 'intermediate' or 'advanced' and `role` is either 'ai-engineer' or 'devops-engineer', sort by `rating_average` descending anf finally get the result count*

**Query string**: `search=azure devops artificial intelligence&$filter=rating_average ge 4.75 and search.in(level, 'advanced|intermediate', '|') and search.in(role, 'ai-engineer|devops-engineer', '|')&$orderby=rating_average desc&$count=true`

**Index**: courses

**Results**:
```json
{
  "@odata.context": "https://corporate-training-search.search.windows.net/indexes('courses-index')/$metadata#docs(*)",
  "@odata.count": 22,
  "value": [
    {
      "@search.score": 4.8391395,
      "Key": "ms-learn13f442b0-f1d1-4402-8c3e-13f0c8b6ce8d",
      "description": "Create an Azure Cognitive Search solution",
      "duration": 63,
      "instructor": "",
      "level": "intermediate",
      "product": "azure-cognitive-search",
      "rating_average": 4.91,
      "rating_count": 45,
      "role": "ai-engineer",
      "source": "MS Learn",
      "title": "Create an Azure Cognitive Search solution",
      "url": "https://docs.microsoft.com/en-us/learn/modules/create-azure-cognitive-search-solution/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "Azure Cognitive Search solution"
      ],
      "instructor_profiles": []
    },
    {
      "@search.score": 6.1224937,
      "Key": "ms-learn62f55c7a-1130-46df-8023-902dde714188",
      "description": "Azure Pipelines help automate building, deploying, and maintaining your applications. While they support a wide range of platforms and programming languages, in this module you’ll focus on using them to implement ASP.NET apps on Azure App Service Web Apps with Azure SQL Database as their data store.",
      "duration": 65,
      "instructor": "",
      "level": "intermediate",
      "product": "azure",
      "rating_average": 4.85,
      "rating_count": 13,
      "role": "devops-engineer",
      "source": "MS Learn",
      "title": "Deploy ASP.NET web apps with Azure Pipelines",
      "url": "https://docs.microsoft.com/en-us/learn/modules/deploy-aspnet-apps-azure-app-service-pipelines/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "Azure App Service Web Apps",
        "ASP.NET apps",
        "Azure SQL Database",
        "Azure Pipelines",
        "wide range",
        "programming languages",
        "data store",
        "applications",
        "platforms",
        "module"
      ],
      "instructor_profiles": []
    },
    {
      "@search.score": 4.461239,
      "Key": "ms-learnf41c2cab-9943-42db-a0c9-8bed47619c53",
      "description": "Create a custom skill for Azure Cognitive Search",
      "duration": 46,
      "instructor": "",
      "level": "intermediate",
      "product": "azure-functions",
      "rating_average": 4.81,
      "rating_count": 31,
      "role": "ai-engineer",
      "source": "MS Learn",
      "title": "Create a custom skill for Azure Cognitive Search",
      "url": "https://docs.microsoft.com/en-us/learn/modules/create-enrichment-pipeline-azure-cognitive-search/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "Azure Cognitive Search",
        "custom skill"
      ],
      "instructor_profiles": []
    },
    {
      "@search.score": 4.380661,
      "Key": "ms-learn7e28c65f-5a23-47e7-b575-66139b3a43ca",
      "description": "Create a custom skill for Azure Cognitive Search",
      "duration": 46,
      "instructor": "",
      "level": "intermediate",
      "product": "azure-cognitive-search",
      "rating_average": 4.81,
      "rating_count": 31,
      "role": "ai-engineer",
      "source": "MS Learn",
      "title": "Create a custom skill for Azure Cognitive Search",
      "url": "https://docs.microsoft.com/en-us/learn/modules/create-enrichment-pipeline-azure-cognitive-search/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "Azure Cognitive Search",
        "custom skill"
      ],
      "instructor_profiles": []
    },
    {
      "@search.score": 4.1042423,
      "Key": "ms-learn0fcb600b-4bb5-480c-97ed-63cf6d842fe8",
      "description": "Create a custom skill for Azure Cognitive Search",
      "duration": 46,
      "instructor": "",
      "level": "intermediate",
      "product": "vs-code",
      "rating_average": 4.81,
      "rating_count": 31,
      "role": "ai-engineer",
      "source": "MS Learn",
      "title": "Create a custom skill for Azure Cognitive Search",
      "url": "https://docs.microsoft.com/en-us/learn/modules/create-enrichment-pipeline-azure-cognitive-search/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "Azure Cognitive Search",
        "custom skill"
      ],
      "instructor_profiles": []
    },
    {
      "@search.score": 4.938952,
      "Key": "ms-learndfd599c0-9e09-4243-b644-483b312430e4",
      "description": "Implement GitHub Actions to build a container image and deploy to Azure Kubernetes Service.",
      "duration": 54,
      "instructor": "",
      "level": "intermediate",
      "product": "azure",
      "rating_average": 4.79,
      "rating_count": 38,
      "role": "devops-engineer",
      "source": "MS Learn",
      "title": "Deploy a cloud-native ASP.NET Core microservice with GitHub Actions",
      "url": "https://docs.microsoft.com/en-us/learn/modules/microservices-devops-aspnet-core/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "Azure Kubernetes Service",
        "GitHub Actions",
        "container image"
      ],
      "instructor_profiles": []
    },
    {
      "@search.score": 4.6936,
      "Key": "ms-learn39ea27c3-ab15-4d7c-b8cd-a3162d940581",
      "description": "Implement GitHub Actions to build a container image and deploy to Azure Kubernetes Service.",
      "duration": 54,
      "instructor": "",
      "level": "intermediate",
      "product": "azure-container-registry",
      "rating_average": 4.79,
      "rating_count": 38,
      "role": "devops-engineer",
      "source": "MS Learn",
      "title": "Deploy a cloud-native ASP.NET Core microservice with GitHub Actions",
      "url": "https://docs.microsoft.com/en-us/learn/modules/microservices-devops-aspnet-core/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "Azure Kubernetes Service",
        "GitHub Actions",
        "container image"
      ],
      "instructor_profiles": []
    },
    {
      "@search.score": 4.6936,
      "Key": "ms-learn49c60335-eda3-463f-95be-b9d32a0e61a3",
      "description": "Implement GitHub Actions to build a container image and deploy to Azure Kubernetes Service.",
      "duration": 54,
      "instructor": "",
      "level": "intermediate",
      "product": "azure-kubernetes-service",
      "rating_average": 4.79,
      "rating_count": 38,
      "role": "devops-engineer",
      "source": "MS Learn",
      "title": "Deploy a cloud-native ASP.NET Core microservice with GitHub Actions",
      "url": "https://docs.microsoft.com/en-us/learn/modules/microservices-devops-aspnet-core/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "Azure Kubernetes Service",
        "GitHub Actions",
        "container image"
      ],
      "instructor_profiles": []
    },
    {
      "@search.score": 4.417181,
      "Key": "ms-learn35be9da9-f514-4659-ae6d-fa0dab3bbe65",
      "description": "Implement GitHub Actions to build a container image and deploy to Azure Kubernetes Service.",
      "duration": 54,
      "instructor": "",
      "level": "intermediate",
      "product": "github",
      "rating_average": 4.79,
      "rating_count": 38,
      "role": "devops-engineer",
      "source": "MS Learn",
      "title": "Deploy a cloud-native ASP.NET Core microservice with GitHub Actions",
      "url": "https://docs.microsoft.com/en-us/learn/modules/microservices-devops-aspnet-core/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "Azure Kubernetes Service",
        "GitHub Actions",
        "container image"
      ],
      "instructor_profiles": []
    },
    {
      "@search.score": 4.417181,
      "Key": "ms-learnbd0400b6-1bc1-41dd-90a3-d05d13df9e62",
      "description": "Implement GitHub Actions to build a container image and deploy to Azure Kubernetes Service.",
      "duration": 54,
      "instructor": "",
      "level": "intermediate",
      "product": "dotnet-core",
      "rating_average": 4.79,
      "rating_count": 38,
      "role": "devops-engineer",
      "source": "MS Learn",
      "title": "Deploy a cloud-native ASP.NET Core microservice with GitHub Actions",
      "url": "https://docs.microsoft.com/en-us/learn/modules/microservices-devops-aspnet-core/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "Azure Kubernetes Service",
        "GitHub Actions",
        "container image"
      ],
      "instructor_profiles": []
    },
    {
      "@search.score": 4.417181,
      "Key": "ms-learnc8f39f5a-47f8-450c-89a2-b38be984c3e6",
      "description": "Implement GitHub Actions to build a container image and deploy to Azure Kubernetes Service.",
      "duration": 54,
      "instructor": "",
      "level": "intermediate",
      "product": "aspnet-core",
      "rating_average": 4.79,
      "rating_count": 38,
      "role": "devops-engineer",
      "source": "MS Learn",
      "title": "Deploy a cloud-native ASP.NET Core microservice with GitHub Actions",
      "url": "https://docs.microsoft.com/en-us/learn/modules/microservices-devops-aspnet-core/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "Azure Kubernetes Service",
        "GitHub Actions",
        "container image"
      ],
      "instructor_profiles": []
    },
    {
      "@search.score": 4.417181,
      "Key": "ms-learnf5559b91-5703-431e-a041-0ec7523625f1",
      "description": "Implement GitHub Actions to build a container image and deploy to Azure Kubernetes Service.",
      "duration": 54,
      "instructor": "",
      "level": "intermediate",
      "product": "dotnet",
      "rating_average": 4.79,
      "rating_count": 38,
      "role": "devops-engineer",
      "source": "MS Learn",
      "title": "Deploy a cloud-native ASP.NET Core microservice with GitHub Actions",
      "url": "https://docs.microsoft.com/en-us/learn/modules/microservices-devops-aspnet-core/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "Azure Kubernetes Service",
        "GitHub Actions",
        "container image"
      ],
      "instructor_profiles": []
    },
    {
      "@search.score": 4.380661,
      "Key": "ms-learn5244e529-28c6-4b6c-bba0-a3edcb956327",
      "description": "Create a knowledge store with Azure Cognitive Search",
      "duration": 46,
      "instructor": "",
      "level": "intermediate",
      "product": "azure-cognitive-search",
      "rating_average": 4.79,
      "rating_count": 42,
      "role": "ai-engineer",
      "source": "MS Learn",
      "title": "Create a knowledge store with Azure Cognitive Search",
      "url": "https://docs.microsoft.com/en-us/learn/modules/create-knowledge-store-azure-cognitive-search/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "Azure Cognitive Search",
        "knowledge store"
      ],
      "instructor_profiles": []
    },
    {
      "@search.score": 2.7133098,
      "Key": "ms-learn4a12759a-5a5c-4112-9213-80b57c78bd8e",
      "description": "Learn to identify valuable information in conversations with LUIS for interpreting user goals (intents) and distill valuable information from sentences (entities).",
      "duration": 27,
      "instructor": "",
      "level": "intermediate",
      "product": "azure-cognitive-services",
      "rating_average": 4.77,
      "rating_count": 131,
      "role": "ai-engineer",
      "source": "MS Learn",
      "title": "Add basic conversational intelligence to your apps by using Language Understanding Intelligent Service (LUIS)",
      "url": "https://docs.microsoft.com/en-us/learn/modules/add-basic-conversational-intelligence/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "valuable information",
        "user goals",
        "conversations",
        "LUIS",
        "intents",
        "sentences",
        "entities"
      ],
      "instructor_profiles": []
    },
    {
      "@search.score": 2.7133098,
      "Key": "ms-learn5bceb6e1-7a21-4905-92ce-3a444cf52340",
      "description": "Learn to identify valuable information in conversations with LUIS for interpreting user goals (intents) and distill valuable information from sentences (entities).",
      "duration": 27,
      "instructor": "",
      "level": "intermediate",
      "product": "azure-language-understanding",
      "rating_average": 4.77,
      "rating_count": 131,
      "role": "ai-engineer",
      "source": "MS Learn",
      "title": "Add basic conversational intelligence to your apps by using Language Understanding Intelligent Service (LUIS)",
      "url": "https://docs.microsoft.com/en-us/learn/modules/add-basic-conversational-intelligence/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "valuable information",
        "user goals",
        "conversations",
        "LUIS",
        "intents",
        "sentences",
        "entities"
      ],
      "instructor_profiles": []
    },
    {
      "@search.score": 1.78057,
      "Key": "ms-learncceb46a6-3b3e-4d84-aa06-aec0aa4621f7",
      "description": "Overview GitHub's products, associated features, and licensing of per-use and metered features.",
      "duration": 19,
      "instructor": "",
      "level": "intermediate",
      "product": "github",
      "rating_average": 4.77,
      "rating_count": 134,
      "role": "devops-engineer",
      "source": "MS Learn",
      "title": "Introduction to GitHub's Products",
      "url": "https://docs.microsoft.com/en-us/learn/modules/github-introduction-products/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "associated features",
        "Overview",
        "GitHub",
        "products",
        "licensing",
        "use",
        "metered"
      ],
      "instructor_profiles": []
    },
    {
      "@search.score": 0.5217709,
      "Key": "ms-learnb65e8df1-b7bb-41e3-a79d-fb3edcd5b323",
      "description": "Learn to manage LUIS apps through versioning, key management, handling data, and improving predictions.",
      "duration": 24,
      "instructor": "",
      "level": "intermediate",
      "product": "azure",
      "rating_average": 4.77,
      "rating_count": 106,
      "role": "ai-engineer",
      "source": "MS Learn",
      "title": "Manage your Language Understanding Intelligent Service (LUIS) Apps",
      "url": "https://docs.microsoft.com/en-us/learn/modules/manage-language-understanding-intelligent-service-apps/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "LUIS apps",
        "key management",
        "versioning",
        "data",
        "predictions"
      ],
      "instructor_profiles": []
    },
    {
      "@search.score": 0.27641892,
      "Key": "ms-learn4ba014cb-90a1-47e6-aef7-ea6a5d19bdf2",
      "description": "Learn to manage LUIS apps through versioning, key management, handling data, and improving predictions.",
      "duration": 24,
      "instructor": "",
      "level": "intermediate",
      "product": "azure-language-understanding",
      "rating_average": 4.77,
      "rating_count": 106,
      "role": "ai-engineer",
      "source": "MS Learn",
      "title": "Manage your Language Understanding Intelligent Service (LUIS) Apps",
      "url": "https://docs.microsoft.com/en-us/learn/modules/manage-language-understanding-intelligent-service-apps/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "LUIS apps",
        "key management",
        "versioning",
        "data",
        "predictions"
      ],
      "instructor_profiles": []
    },
    {
      "@search.score": 0.27641892,
      "Key": "ms-learnf636850f-02f7-4cc6-ab0a-f4cb238bd816",
      "description": "Learn to manage LUIS apps through versioning, key management, handling data, and improving predictions.",
      "duration": 24,
      "instructor": "",
      "level": "intermediate",
      "product": "azure-cognitive-services",
      "rating_average": 4.77,
      "rating_count": 106,
      "role": "ai-engineer",
      "source": "MS Learn",
      "title": "Manage your Language Understanding Intelligent Service (LUIS) Apps",
      "url": "https://docs.microsoft.com/en-us/learn/modules/manage-language-understanding-intelligent-service-apps/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "LUIS apps",
        "key management",
        "versioning",
        "data",
        "predictions"
      ],
      "instructor_profiles": []
    },
    {
      "@search.score": 0.5217709,
      "Key": "ms-learn01731c10-20bb-41e7-ba21-8528669dcdc3",
      "description": "Use containers for your Language Understanding Intelligent Service (LUIS) Apps",
      "duration": 18,
      "instructor": "",
      "level": "advanced",
      "product": "azure",
      "rating_average": 4.75,
      "rating_count": 137,
      "role": "ai-engineer",
      "source": "MS Learn",
      "title": "Use containers for your Language Understanding Intelligent Service (LUIS) Apps",
      "url": "https://docs.microsoft.com/en-us/learn/modules/use-containers-language-understanding-intelligent-service-apps/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "Language Understanding Intelligent Service",
        "LUIS) Apps",
        "containers"
      ],
      "instructor_profiles": []
    },
    {
      "@search.score": 0.27641892,
      "Key": "ms-learnb5a079db-8f56-4414-8762-92ea7691d6bf",
      "description": "Use containers for your Language Understanding Intelligent Service (LUIS) Apps",
      "duration": 18,
      "instructor": "",
      "level": "advanced",
      "product": "azure-language-understanding",
      "rating_average": 4.75,
      "rating_count": 137,
      "role": "ai-engineer",
      "source": "MS Learn",
      "title": "Use containers for your Language Understanding Intelligent Service (LUIS) Apps",
      "url": "https://docs.microsoft.com/en-us/learn/modules/use-containers-language-understanding-intelligent-service-apps/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "Language Understanding Intelligent Service",
        "LUIS) Apps",
        "containers"
      ],
      "instructor_profiles": []
    },
    {
      "@search.score": 0.27641892,
      "Key": "ms-learnc975e981-df18-44b6-9b16-e8ed3ed7de98",
      "description": "Use containers for your Language Understanding Intelligent Service (LUIS) Apps",
      "duration": 18,
      "instructor": "",
      "level": "advanced",
      "product": "azure-cognitive-services",
      "rating_average": 4.75,
      "rating_count": 137,
      "role": "ai-engineer",
      "source": "MS Learn",
      "title": "Use containers for your Language Understanding Intelligent Service (LUIS) Apps",
      "url": "https://docs.microsoft.com/en-us/learn/modules/use-containers-language-understanding-intelligent-service-apps/?WT.mc_id=api_CatalogApi",
      "keyphrases": [
        "Language Understanding Intelligent Service",
        "LUIS) Apps",
        "containers"
      ],
      "instructor_profiles": []
    }
  ]
}
```

---

### Query 3

**Description**: *Search for "Claudia" (instructor), get facets for `level`, `role`, `source` and `instructor` and also get the result count*

**Query string**: `search=student intermediate&$filter=rating_average ge 4 and search.in(instructor, 'Eileen Diaz', '|')&$orderby=duration desc&$count=true`

**Index**: courses

**Results**:
```json
{
  "@odata.context": "https://corporate-training-search.search.windows.net/indexes('courses-index')/$metadata#docs(*)",
  "@odata.count": 2,
  "value": [
    {
      "@search.score": 1.1114495,
      "Key": "company-moodled3f0c955-ac6e-4ced-b91b-ffcef3e8cede",
      "description": "For developers, learn our best practices for writing secure code for web, server, and desktop development",
      "duration": 3,
      "instructor": "Eileen Diaz",
      "level": "intermediate",
      "product": "NA",
      "rating_average": 4.4,
      "rating_count": 132,
      "role": "developer",
      "source": "Company Moodle",
      "title": "Code security",
      "url": "https://www.example.com/course9",
      "keyphrases": [
        "best practices",
        "secure code",
        "desktop development",
        "developers",
        "web",
        "server"
      ],
      "instructor_profiles": [
        {
          "name": "Eileen Diaz",
          "description": "Eileen is our Senior Security Engineer responsible for application and service security. She has been with the company for 9 years and enjoys writing Sci-Fi in her spare time."
        }
      ]
    },
    {
      "@search.score": 1.1114495,
      "Key": "company-moodle6b5d3f55-eb02-499d-9775-2e0e25659e07",
      "description": "Learn our company's Principles for the Responsible Use of AI",
      "duration": 1,
      "instructor": "Eileen Diaz",
      "level": "intermediate",
      "product": "NA",
      "rating_average": 4.3,
      "rating_count": 24,
      "role": "architect",
      "source": "Company Moodle",
      "title": "Ethics in AI",
      "url": "https://www.example.com/course12",
      "keyphrases": [
        "Responsible Use",
        "company",
        "Principles",
        "AI"
      ],
      "instructor_profiles": [
        {
          "name": "Eileen Diaz",
          "description": "Eileen is our Senior Security Engineer responsible for application and service security. She has been with the company for 9 years and enjoys writing Sci-Fi in her spare time."
        }
      ]
    }
  ]
}
```

### Query 4

**Description**: *Select author, title, keyphrases, publication name, DOI and publication date from all papers where the title contains the word "review"*

**Query string**: `$select=author,title,keyphrases,publicationName,doi,publicationDate&$filter=search.ismatch('review', 'title')`

**Index**: library

**Results**:
```json
{
  "@odata.context": "https://corporate-training-search.search.windows.net/indexes('papers-index')/$metadata#docs(*)",
  "value": [
    {
      "@search.score": 1,
      "keyphrases": [
        "systematic review",
        "algorithmic decision-making",
        "HR recruitment",
        "HR development",
        "discrimination",
        "fairness",
        "context"
      ],
      "title": "Discriminated by an algorithm: a systematic review of discrimination and fairness by algorithmic decision-making in the context of HR recruitment and HR development",
      "author": "Alina Köchling ",
      "publicationName": "Business Research",
      "doi": "10.1007/s40685-020-00134-w",
      "publicationDate": "2020-11-01"
    },
    {
      "@search.score": 1,
      "keyphrases": [
        "Mining aspects",
        "social network",
        "customer",
        "review"
      ],
      "title": "Mining aspects of customer’s review on the social network",
      "author": "Tu Nguyen Thi Ngoc ",
      "publicationName": "Journal of Big Data",
      "doi": "10.1186/s40537-019-0184-5",
      "publicationDate": "2019-02-28"
    },
    {
      "@search.score": 1,
      "keyphrases": [
        "Big data stream analysis",
        "systematic literature review"
      ],
      "title": "Big data stream analysis: a systematic literature review",
      "author": "Taiwo Kolajo ",
      "publicationName": "Journal of Big Data",
      "doi": "10.1186/s40537-019-0210-7",
      "publicationDate": "2019-06-06"
    },
    {
      "@search.score": 1,
      "keyphrases": [
        "Technological advancements",
        "systematic review",
        "opportunities",
        "Neuromarketing"
      ],
      "title": "Technological advancements and opportunities in Neuromarketing: a systematic review",
      "author": "Ferdousi Sabera Rawnaque ",
      "publicationName": "Brain Informatics",
      "doi": "10.1186/s40708-020-00109-x",
      "publicationDate": "2020-09-21"
    }
  ]
}
```

---

### Query 5

**Description**: *Select author, title, content, keyphrases, publication name, DOI and publication date from all documents having the 'analysis' or 'ai' keyphrase, and get the result count*

**Query string**: `$select=author,title,content,keyphrases,publicationName,doi,publicationDate&$filter=keyphrases/any(kp: search.in(kp, 'analysis, ai'))&$count=true`

**Index**: library

**Results**:
```json
{
  "@odata.context": "https://corporate-training-search.search.windows.net/indexes('papers-index')/$metadata#docs(*)",
  "@odata.count": 1,
  "value": [
    {
      "@search.score": 1,
      "content": "\nChandrasekaran and Esfandiari Journal of Trust Management  (2015) 2:8 \nDOI 10.1186/s40493-015-0019-z\n\nRESEARCH Open Access\n\nToward a testbed for evaluating\ncomputational trust models: experiments\nand analysis\nPartheeban Chandrasekaran and Babak Esfandiari*\n\n*Correspondence:\nbabak@sce.carleton.ca\nDepartment of Systems and\nComputer Engineering, Carleton\nUniversity, 1125 Colonel By Drive,\nOttawa, Ontario K1s5B6, Canada\n\nAbstract\nWe propose a generic testbed for evaluating social trust models and we show how\nexisting models can fit our tesbed. To showcase the flexibility of our design, we\nimplemented a prototype and evaluated three trust algorithms, namely EigenTrust,\nPeerTrust and Appleseed, for their vulnerabilites to attacks and compliance to various\ntrust properties. For example, we were able to exhibit discrepancies between\nEigenTrust and PeerTrust, as well as trade-offs between resistance to slandering attacks\nversus self-promotion.\n\nKeywords: Trust testbed; Reputation; Multi-agent systems\n\nIntroduction\nMotivation\n\nWith the growth of online community-based systems such as peer-to-peer file-sharing\napplications, e-commerce and social networking websites, there is an increasing need to\nprovide computational trust mechanisms to determine which users or agents are honest\nand which ones are malicious. Many models calculate trust by relying on analyzing a\nhistory of interactions. The calculations can range from the simple averaging of ratings\non eBay to flow-based scores in the Advogato website. Thus for a researcher to evaluate\nand compare his or her latest model against existing ones, a comprehensive test tool is\nneeded. However, our research shows that the tools that exist to assist researchers are not\nflexible enough to include different trust models and their evaluations. Moreover, these\ntools use their own set of application-dependent metrics to evaluate a reputation system.\nThis means that a number of trust models cannot be evaluated for vulnerabilities against\ncertain types of attacks. Thus, there is still a need for a generic testbed to evaluate and\ncompare computational trust models.\n\nOverview of our solution and contributions\n\nIn this paper, we present a model and a testbed for evaluating a family of trust algo-\nrithms that rely on past transactions between agents. Trust assessment is viewed as a\nprocess consisting of a succession of graph transformations, where the agents form the\nvertices of the graph. The meaning of the edges depends on the transformation stage,\n\n© 2015 Chandrasekaran and Esfandiari. Open Access This article is distributed under the terms of the Creative Commons\nAttribution 4.0 International License (http://creativecommons.org/licenses/by/4.0/), which permits unrestricted use, distribution,\nand reproduction in any medium, provided you give appropriate credit to the original author(s) and the source, provide a link to\nthe Creative Commons license, and indicate if changes were made.\n\nhttp://crossmark.crossref.org/dialog/?doi=10.1186/s40493-015-0019-z-x&domain=pdf\nmailto: babak@sce.carleton.ca\nhttp://creativecommons.org/licenses/by/4.0/\n\n\nChandrasekaran and Esfandiari Journal of Trust Management  (2015) 2:8 Page 2 of 27\n\nand can refer to the presence of transactions between the two agents or the existence\nof a trust relationship between them. Our first contribution is to show that with this\nview, existing reputation systems can be adopted under a single model, but they work at\ndifferent stages of the trust assessment workflow. This allows us to present a new classi-\nfication scheme for a number of trust models based on where they fit in the assessment\nworkflow. The second contribution of our work is that this workflow can be described\nformally, and by doing this, we show that it is possible to model a variety of attacks\nand evaluation schemes. Finally, out of the larger number of systems we classified, we\nselected three reputation systems, namely EigenTrust [1], PeerTrust [2] and Appleseed\n[3], to exemplify the range and variety of reputation systems that our testbed can accom-\nmodate. We evaluated these three systems in our testbed against simple attacks and\nwe validated their compliance to basic trust properties. In particular, we were able to\nexhibit differences in the way EigenTrust and PeerTrust rank the agents, we observed\nthe subtle interplay between slandering and self-promoting attacks (higher sensitivity\nto one attack can lead to lower sensitivity to the other), and we verified that trust\nweakens along a friend-of-a-friend chain and that it is more easily lost than gained\n(as it should be).\n\nOrganization\n\nThis article is organized as follows: section ‘Background and literature review’ provides\nbackground and state of the art on trust models, attacks against them, and existing\ntestbeds for evaluation. Section ‘Problem description and model’ formulates the research\nproblem of this article and proposes our model for a testbed. Section ‘Classifying and\nchaining algorithms’ shows how some of existing trust algorithms can fit our model, and\nhow one can combine or compare them using our model and testbed. Section ‘Results and\ndiscussion’ describes the implementation details of our testbed prototype and presents\nevaluation results of three different trust algorithms, namely EigenTrust, PeerTrust, and\nAppleseed. Section ‘Conclusions’ concludes this article and summarizes the contributions\nand limitations of our work.\n\nBackground and literature review\nSocial trust models\n\nTrust management systems aid agents in establishing and assessing mutual trust. How-\never, the actual mechanisms used in these systems vary. For example, public key infras-\ntructures [4] rely on certificates whereas reputation-based trust management systems are\nbased on experiences of earlier direct and indirect interactions [5].\nIn this paper we will focus on social trust models based on reputation. The trust model\n\nshould provide a means to compare the trustworthiness of agents in order to choose a\nparticular agent to perform an action. For instance, on an e-commerce website like eBay,\nwe need to be able to compare the trustworthiness of sellers in order to pick the most\ntrustworthy one to buy a product from.\nSocial trust models rely on past experiences of agents to produce trust assertions. That\n\nis, the agents in the system interact with each other and record their experiences, which\nare then used to determine whether a particular agent is trustworthy. This model is self-\nsufficient because it does not rely on a third party to propagate trust, like it would in\ncertificate authority-based PKI trust models. However, there are drawbacks to having no\n\n\n\nChandrasekaran and Esfandiari Journal of Trust Management  (2015) 2:8 Page 3 of 27\n\nroot of trust. For instance, agents evaluating the trustworthiness of agents with whom\nthere has been no interaction must use recommendations from others and, in turn,\nevaluate the trustworthiness of the recommenders. Social trust models must address this\nproblem.\n\nNature of input\n\nVarious inputs are used by social trust algorithms to measure the trustworthiness of\nagents. In EigenTrust [1], PeerTrust [2], TRAVOS [6] and Beta Reputation System (BRS)\n[7], agents rate their satisfaction after a transaction (e.g., downloading a file in a P2P\nfile-sharing network). These ratings are used to obtain a trust score that represents the\ntrustworthiness of the agent. In Aberer and Despotovic’s system [5]1, agents may file com-\nplaints (can be seen as dissatisfaction) about each other after a transaction. In Advogato\n[8], whose goal is to discourage spam on its blogging website, users explicitly certify\neach other as belonging to a particular level in the community. Trust algorithms may\nalso directly use trust scores among agents to compute an aggregated trustworthiness\nof agents, as in TidalTrust [9] and Appleseed [3]. In the specific context of P2P file-\nsharing, Credence [10] uses the votes on file authenticity to calculate a similarity score\nbetween agents and uses it to measure trust. The trust score is then used to recommend\nfiles.\n\nDirect vs. indirect trust\n\nThe truster may use some or all of its own and other agents’ past experiences with the\ntrustee to obtain a trust score. Trust algorithms often use gossiping to poll agents with\nwhom the truster has had interactions in the past.\nThe trust score calculated using only the experiences from direct interactions is\n\ncalled the direct trust score, while the trust score calculated using the recommenda-\ntions from other agents is called the indirect trust score [11]. As mentioned earlier,\nreputation systems use different inputs (satisfaction ratings, votes, certificates, etc.) to\ncalculate direct trust scores and indirect trust scores. PeerTrust uses satisfaction ratings\nto calculate both direct and indirect trust scores, whereas EigenTrust and TRAVOS\nuse satisfaction ratings to calculate direct trust scores, which they then use to calcu-\nlate indirect trust scores. Therefore, we can categorize the trust algorithms based on\nthe input required. But how do trust algorithms calculate the trust scores of agents\nusing the above information? It again varies from algorithm to algorithm. For instance,\nPeerTrust, EigenTrust, and Aberer use simple averaging of ratings, TRAVOS and BRS\nuse the beta probability density function, and Appleseed uses the Spreading Activation\nmodel.\n\nGlobal vs. local trust\n\nThe trust algorithm may output a global trust score or a local trust score [3, 12]. A global\ntrust score is one that represents the general trust that all agents have on a particular\nagent, whereas local trust scores represents the trust from the perspective of the truster\nand thus each truster may trust an agent differently. In our survey, we found PeerTrust,\nEigenTrust, and Aberer to be global trust algorithms whereas TRAVOS, BRS, Credence,\nAdvogato, TidalTrust, Appleseed, Marsh [13] and Abdul-Rahman [14] are local trust\nalgorithms.\n\n\n\nChandrasekaran and Esfandiari Journal of Trust Management  (2015) 2:8 Page 4 of 27\n\nTo trust or not to trust\n\nOnce the trust score is calculated, it can be used to decide whether to trust the agent. It\ncan be as simple as comparing the trust score against a threshold: if the trust score is above\na certain threshold, then the agent is trusted. Marsh [13], and Aberer [5] use thresholding\ntechniques. If the trust algorithm outputs normalized trust scores of agents as in Eigen-\nTrust, then the trust scores of agents are ranked. In this case, one may consider a certain\npercentage of the top ranked agents as trustworthy. In Appleseed, a graph is first obtained\nwith trust scores of agents as edge weights, and then, the truster agent is “injected” with\na value called the activation energy. This energy is spread to agents with a spreading fac-\ntor along the edges in the graph and the algorithm ranks the agents according to their\ntrust scores. Trust decisions can also be flow-based such as in Advogato, which calculates\na maximum “flow of trust” in the trust graph to determine which agents are trustworthy\nand which are not.\nIn short, social trust models focus on the following:\n\n1. What is the input to calculate the trust score of an agent?\n2. Does the trust algorithm use only direct experience or does it also rely on third\n\nparty recommendations?\n3. Is the trust score of an agent global or local?\n4. How does one decide whether to trust an agent?\n\nGiven the above discussion, and to assess the scope of our testbed, we propose tomodel,\nevaluate and compare three algorithms from fairly different families. The next sections\nprovide detailed descriptions of the trust models we selected and that we implemented in\nour testbed. The details are given to help understand the output of our experiments, but\nreaders familiar with EigenTrust, PeerTrust and/or AppleSeed may skip those respective\nsections.\n\nPeerTrust\n\nIn PeerTrust, agents rate each other in terms of the satisfaction received. These ratings\nare weighted by trust scores of the raters, and a global trust score is computed recursively\nusing Eq. 2.1, where:\n\n• T(u) is the trust score of agent u\n• I(u) is the set of transactions that agent u had with all the agents in the system\n• S(u, i) is the satisfaction rating on u for transaction i\n• p(u, i) is the agent that provided the rating.\n\nT(u) =\nI(u)∑\ni=1\n\nS(u, i) × T(p(u, i))∑I(u)\nj=1 T(p(u, j))\n\n(2.1)\n\nPeerTrust also provides a method for calculating local trust scores. In both local and\nglobal trust score computations, the trust score is compared against a threshold to decide\nwhether to trust or not.\n\nEigenTrust\n\nAgents in EigenTrust rate transactions as satisfactory or unsatisfactory [1]. These trans-\naction ratings are used as input, to calculate a local direct trust score, from which a global\ntrust score is then calculated.\n\n\n\nChandrasekaran and Esfandiari Journal of Trust Management  (2015) 2:8 Page 5 of 27\n\nAn agent i calculates the normalized local trust score of agent j, as shown in Eq. 2.2,\nwhere tij ∈ {+1,−1} is the transaction rating, and sij is the sum of ratings.\n\nsij =\n∑\nTij\n\ntrij\n\ncij = max(sij, 0)∑\nk max(sik , 0)\n\n(2.2)\n\nNote that we cannot use sij as the local trust score without normalizing, because mali-\ncious agents can arbitrarily assign high local trust values to fellow malicious agents and\nlow local trust values to honest agents.\nTo calculate the global trust score of an agent, the truster queries his friends for their\n\ntrust scores on the trustee. These local trust scores are aggregated, as shown in Eq. 2.3.\n\ntik =\n∑\nj\ncijcjk (2.3)\n\nIf we let C be the matrix containing cij elements, �ci be the local trust vector for i (each\nelement corresponds to the trust that i has in j), and �ti the vector containing tik , then,\n\n�ti = CT �ci (2.4)\n\nBy asking a friend’s friend’s opinion, Eq. 2.4 becomes �ti = (CT )2 �ci. If an agent keeps\nasking the opinions of its friends of friends, the whole trust graph can be explored, and\nEq. 2.4 becomes Eq. 2.5, where n is the number of hops from i.\n\n�t = (CT )n �ci (2.5)\n\nThe trust scores of the agents converge to a global value irrespective of the trustee.\nBecause EigenTrust outputs global trust scores (normalized over the sum of all agents),\n\nagents are ranked according to their trust scores (unlike PeerTrust). Therefore, an agent\nis considered trustworthy if it is within a certain rank.\n\nAppleseed\n\nAppleseed is a flow-based algorithm [3]. Assuming that we are given a directed weighted\ngraph with agents as nodes, edges as trust relationships, and the weight of an edge as\ntrustworthiness of the sink, we can determine the amount of trust that flows in the graph.\nThat is, given a trust seed, an energy in ∈ R\n\n+\n0 , spreading factor decay ∈[ 0, 1], and conver-\n\ngence threshold Tc, Appleseed returns a trust score of agents from the perspective of the\ntrust seed.\nThe trust propagation from agent a to agent b is determined using Eq. 2.6, where the\n\nweight of edge (a, b) represents the amount of trust a places in b, and in(a) and in(b)\nrepresent the flow of trust into a and b, respectively.\n\nin(b) = decay ×\n∑\n\n(a,b)∈E\nin(a) × weight(a, b)∑\n\n(a,c)∈E weight(a, c)\n(2.6)\n\nThe trust of an agent b (trust(b)) is then updated using Eq. 2.7, where the decay factor\nensures that trust in an agent decreases as the path length from the seed increases.\n\ntrust(b) := trust(b) + (1 − decay) × in(b) (2.7)\n\n\n\nChandrasekaran and Esfandiari Journal of Trust Management  (2015) 2:8 Page 6 of 27\n\nGenerally, trust graphs have loops, which makes Eq. 2.7 recursive. Thus a termination\ncondition like the one below is required, where Ai ⊆ A is the set of nodes that were\ndiscovered until step i and trusti(x) is the current trust scores for all x ∈ Ai:\n\n∀x ∈ Ai : trusti(x) − trusti−1(x) ≤ Tc (2.8)\n\nAfter Eq. 2.7 terminates, the trust scores of agents are ranked. Since this set is ranked\nfrom the perspective of the seed, Appleseed is a local trust algorithm.\nAs our brief survey shows, the trust models vary in terms of their input, output, and\n\nthe methods they use. To evaluate and compare them, testbeds are needed. In the next\nsection we take a look at existing testbeds.\n\nTestbeds\n\nWe investigated two testbed models, namely Guha’s [15] andMacau [16], and two testbed\nimplementations, namely ART [17] and TREET [18], which are used to evaluate trust\nalgorithms. This section provides details of our investigation.\n\nGuha\n\nGuha [15] proposes a model to capture document recommendation systems, where trust\nand reputation play an important role. The model relies on a graph of agents where the\nedges can be weighted based on their mutual ratings, and a rating function for documents\nby agents. Guha then discusses how trust can be calculated based on those ratings, and\nevaluates a few case studies of real systems that can be accommodated by the model.\nGuha’s model can capture trust systems that take a set of documents and their ratings\n\nas input (such as Credence [10]), but it cannot accommodate systems where the only\ninput consists of direct feedbacks between agents, such as in PeerTrust (global) [2] or\nEigenTrust [1]. Also, the rating of documents is itself an output of Guha’s model, and that\nis often not the purpose or output of many more general-purpose trust models.\nIn short, document recommendation systems can be viewed as a specialization or\n\nsubclass of more general trust systems, and Guha’s model is suitable for that subclass.\n\nMacau\n\nHazard and Singh’s Macau [16] is a model for evaluating reputation systems. The authors\ndistinguish two roles for any agent: a rater that evaluates a target. Transactions are viewed\nas a favor provided by the target to the rater. The target’s reputation, local to each rater-\ntarget pairing, is updated after each transaction and depends on the previous reputation\nvalue. The target’s payoff in giving a favor is also dependent on its current reputation but\nalso on its belief of the likelihood that the rater will in turn return the favor in the future.\nBased on the above definitions, the authors define a set of desirable properties for a\n\nreputation system:\n\n• Monotonicity: given two different targets a and b, the computed reputation of a\nshould be higher than that of b if the predicted payoff of a transaction with a is\nhigher than with b.\n\n• Unambiguity and convergence: the reputation should converge over time to a single\nfixpoint, regardless of its initial value.\n\n• Accuracy: this convergence should happen quickly, thus minimizing the total\nreputation estimation errors in the meantime.\n\n\n\nChandrasekaran and Esfandiari Journal of Trust Management  (2015) 2:8 Page 7 of 27\n\nMacau thus captures an important stage in trust assessment, i.e. the update of one-to-\none trustworthiness based on past transactions. It has been used to evaluate, in terms of\ntheir compliance to the properties defined above, algorithms such as TRAVOS [6] and the\nBeta Reputation System (BRS) [7] that model positive and negative experiences as ran-\ndom variables following a beta probability distribution. The comparison of trust models\nrelying on the beta distribution and their resilience to various attacks has also recently\nbeen explored in [19].\n\nART\n\nThe Agent Reputation and Trust testbed (ART) [17] provides an open-source message-\ndriven simulation engine for implementing and comparing the performance of reputation\nsystems. ART uses art painting sales as the domain.\nEach client has to sell paintings belonging to a particular era. To determine their\n\nmarket values, clients refer to agents for appraisals for a fee. Because each agent\nis an expert only in a specific era, it may not be able to provide appraisals for\npaintings from other eras and therefore refers to other agents for a fee. After such\ninteractions, agents record their experiences, calculate their reputation scores, and\nuse them to choose the most trustworthy agents for future interactions. The goal\nof each agent is to finish the simulation with the highest bank balance, and, intu-\nitively, the winning agent’s trust mechanism knows the right agents to trust for\nrecommendations.\nThe ART testbed provides a protocol that each agent must implement. The protocol\n\nspecifies the possible messages that agents can send to each other. Themessages are deliv-\nered by the simulation engine, which loops over each agent at every time interval. The\nengine is also responsible for keeping track of the bank balance of the agents, and assign-\ning new clients to agents. All results are collected and stored in a database and displayed\non a graphical user interface (GUI) at runtime.\nART is best suited for evaluating trust calculation schemes from a first person point\n\nof view. It is not meant as a platform for testing trust management as a service provided\nby the system. For example, to evaluate EigenTrust in ART, one would either need to\nconsiderably modify ART itself (for the centralized version of EigenTrust) or to require\ncooperation from the participating agents and an additional dedicated distributed infras-\ntructure (for the distributed version). Furthermore, as also pointed out in [16] and [20],\nthe comparison of the performance of different agents is not necessarily based on their\ncorrect ability to assess the reputation of other agents, but rather based on how well they\nmodel and exploit the problem domain.\n\nTREET\n\nThe Trust and Reputation Experimentation and Evaluation Testbed (TREET) [18] mod-\nels a general marketplace scenario where there are buyers, sellers, and 1,000 different\nproducts with varying prices, such that there are more inexpensive items than expensive\nones. The sale price of the products is fixed, to avoid the influence of market competition.\nThe cost of producing an item is 75% of the selling price, and the seller incurs this cost.\nTo lower this cost and increase profit, a seller can cheat by not shipping the item. Each\nproduct also has a utility value of 110% of the selling price, which encourages buyers to\npurchase.\n\n\n\nChandrasekaran and Esfandiari Journal of Trust Management  (2015) 2:8 Page 8 of 27\n\nAgents join or exit after 100 simulation days or after a day with a probability of 0.05,\nbut to keep the number of buyers and sellers constant, an agent is introduced for each\ndeparting agent. At initialization, each seller is assigned a random number of products\nto sell. Buyers evaluate the offers from each seller and pick a seller. Sellers are informed\nof the accepted offers and are paid. Fourteen days after a sale, the buyer knows whether\nhe has been cheated or not, depending on whether he receives the purchased item. The\nbuyer then provides feedback based on his experience of the transaction. The feedback is\nin turn used to choose sellers for future transactions.\nTREET evaluates the performance of various reputation systems under Reputation Lag\n\nattack, Proliferation attack, and Value Imbalance attack using the following metrics:\n\n1. cheater sales over honest sales ratio\n2. cheater profit over honest profit ratio\n\nMultiple seller accounts are needed to orchestrate a Proliferation Attack, but TREET\ndoes not consider attacks such as White-Washing and Self-Promoting, which require\ncreating multiple buyer accounts.\nTREET addresses many of ART’s limitation in a marketplace scenario. To name a\n\nfew [21], TREET supports both centralized and decentralized trust algorithms, allows\ncollusion attacks to be implemented, and does not put a restriction on trust score rep-\nresentation. However, like ART, the evaluation metrics in TREET are tightly coupled to\nthe marketplace domain. It is unclear how ART or TREET can be used to evaluate trust\nmodels used in other systems, such as P2P file-sharing networks, online product review\nwebsites and others that use trust. To our knowledge, there is no testbed that provides\ngeneric evaluation metrics and that is independent of the application domain.\n\nSummary\n\nTrust is a tool used in the decision-making process and it can be computed. There are\nmanymodels based on social trust that attempt to aid agents in making rational decisions.\nHowever, these models vary in terms of their input and output requirements. This makes\nevaluations against a common set of attacks difficult.\n\nProblem description andmodel\nOur goal is to have a testbed that is generic enough to accommodate as many trust\nmanagement systems and models as possible. Our requirements are:\n\n1. A model that provides an abstraction layer for developers to incorporate existing\nand new systems that match the input and output of the model.\n\n2. An evaluation framework to measure and compare the performance of trust models\nagainst trust properties and attacks independently of the application domain.\n\nIn this section, we introduce an abstract model for trust management systems. This\nmodel will be the foundation of our testbed. Our model is essentially based on the\nfollowing stages:\n\n1. In stage 1 of the trust assessment process, the feedback provided by agents on other\nagents is represented as a feedback history graph.\n\n\n\nChandrasekaran and Esfandiari Journal of Trust Management  (2015) 2:8 Page 9 of 27\n\n2. In stage 2, a reputation graph is produced, where the weight of an arc denotes the\nreputation of the target agent. “Reputation” here follows [14], as “an expectation\nabout an individual’s behavior based on information about or observations of its\npast behavior”. It is viewed as an estimation of trustworthiness based on a\ncombination of direct and indirect feedback.\n\n3. In the final stage, a trust graph is produced, where the existence of an arc implies\ntrust in the target agent. We take “trust” here to mean the “belief by agent A that\nagent B is trustworthy” [2, 22], and so it is boolean and subjective in our model.\n\nIn the rest of this section, we define the aforementioned graphs in stages.\n\nStage 1—obtain feedback history graph\n\nWe first define a feedback, f (a, b) ∈ R as an assessment made by agent a of an action or\ngroup of actions performed by agent b, where a and b belong to the set A of all the agents\nin the system. The list of n feedbacks by a on b, FHG(a, b), is called a feedback history,\nrepresented as follows:\n\nFHG(a, b) �→ (f1(a, b), f2(a, b), . . . , fn(a, b)) (3.1)\n\nThe feedback fi(a, b) indicates the ith satisfaction received by a from b’s action. For\nexample, in a file-sharing network, the feedback by a downloader may indicate the sat-\nisfaction received from downloading a file from an uploader in terms of a value in R.\nExisting trust models use different ranges of values for feedback, and letting the feedback\nvalue be in R allows us to include these reputation systems in our testbed.\nIf A is the set of agents, E is the set of labelled arcs (a, b), and the label is FHG(a, b)\n\nwhen FHG(a, b) \t= ∅, then the feedback histories for all agents in A are represented in a\ndirected and labelled graph called Feedback History Graph (FHG)2, FHG = (A,E):\n\nFHG : A × A → R\nN\n\n∗\n(3.2)\n\nNote that we have not included timestamps associated with each feedback (which would\nbe useful for, among other things, running our testbed as a discrete event simulator), but\nour model can be expanded to accommodate it.\nOnce the feedback history graph is obtained, the next step is to produce a reputation\n\ngraph.\n\nStage 2—obtain reputation graph\n\nA Reputation Graph (RG), RG = (A,E′\n), is a directed and weighted graph, where the\n\nweight on an arc, RG(a, b), is the trustworthiness of b from a’s perspective:\n\nRG : A × A → R (3.3)\n\nThe edges are added by computing second and nth-hand trust via transitive closure of\nedges in E. That is: if (a, b) ∈ E and (b, c) ∈ E ⇒ (a, b), (b, c), and (a, c) ∈ E′ (the value of\nthe weight of the edges, however, depends on the particular trust algorithm).\nReputation algorithms may also exhibit the reflexive property by adding looping arcs to\n\nindicate that the truster trusts itself to a certain degree for a particular task [1–3].\nThe existing literature categorizes reputation algorithms into two groups: local and\n\nglobal (Figs. 1(a) and (b), respectively) [3, 5]. Global algorithms assign a single reputa-\ntion score to each agent. Therefore, if a global algorithm is used, then the weights of the\n\n\n\nChandrasekaran and Esfandiari Journal of Trust Management  (2015) 2:8 Page 10 of 27\n\nFig. 1 Examples of reputation graphs output respectively by a local and global algorithm\n\nincoming arcs of an agent should be the same, as shown in Fig. 1(b) (although for clar-\nity’s sake we will often present the graph simply as a ranking of agents in the rest of this\narticle). There is no such property for local algorithms.\nReputation algorithms may also differ in how the graphs is produced. One method is\n\nto first calculate one-to-one scores of agents using direct feedbacks and then use them\nto calculate the trustworthiness of agents previously unknown to the truster (e.g., Eigen-\nTrust). This is shown as 1a and 1b in Fig. 2. The other method (#2 in Fig. 2) skips the\nintermediate graph in the aforementioned method and produces a reputation graph (e.g.,\nPeerTrust).\n\nStage 3—obtain trust graph\n\nThe graph obtained in stage 2 contains information about the trustworthiness of agents.\nBut to use this information to make a decision about a transaction in the future, agents\nmust convert trustworthiness to boolean trust (see [23] for an example), which can also\nbe expressed as a graph. We refer to this directed graph as the Trust Graph (TG) TG =\n(A, F), where a directed edge ab ∈ F represents agent a trusting agent b.\nTo summarize ourmodel, we can represent the stages as part of a workflow as illustrated\n\nin Fig. 3.\n\nFig. 2 Two methods to obtain a reputation graph\n\n\n\nChandrasekaran and Esfandiari Journal of Trust Management  (2015) 2:8 Page 11 of 27\n\nFig. 3 Overview of the stages in our model\n\nIn the next section, we see at what stages in our model do various algorithms fit, and\ndescribe criteria for chaining different algorithms.\n\nClassifying and chaining algorithms\nBy refactoring the trust models according to the stages presented in the above sections,\nwe start to see a new classification scheme. Let us take EigenTrust, PeerTrust, and Apple-\nseed as examples and describe them using our model. EigenTrust takes an FHG with\nedge labels in {0, 1}∗ as input and outputs an RG with edge labels in [ 0, 1]. PeerTrust,\non the other hand, takes an FHG with edge labels in [ 0, 1]∗ as input and outputs an\nRG with edge labels in [ 0, 1]. Meanwhile, Appleseed requires an RG with edge labels in\n[ 0, 1] as input and outputs another RG′ in the same codomain. It is also possible for an\nalgorithm to skip some stages. For example, according to our model, Aberer [5] skips\nstage 2 and does not output a reputation graph. One can also represent simple mecha-\nnisms to generate a trust graph by applying a threshold on reputation values (as output\nfor example by EigenTrust), or by selecting the top k agents. This stage transitions of\nalgorithms are depicted3 in Fig. 4. In addition to the existing classification criteria in the\nstate of the art, trust algorithms can now be classified according to their stage transi-\ntions (i.e., from one stage to another as well as transitioning within a stage) as shown in\nTable 1.\nIt is important to note that although these three algorithms output a reputation\n\ngraph with continuous reputation values between 0 and 1, the semantics of these val-\nues are different. EigenTrust outputs relative (among agents) global reputation scores,\nPeerTrust outputs an absolute global reputation score, and Appleseed produces relative\nlocal reputation scores. In other words, EigenTrust and Appleseed are ranking algorithms\n(global and local, respectively), whereas PeerTrust is not.\n\n\n\nChandrasekaran and Esfandiari Journal of Trust Management  (2015) 2:8 Page 12 of 27\n\nFig. 4 Stage transitions of Trust algorithms\n\nAs we can see, each step of the trust assessment process can be viewed as a\ngraph transformation function, and we can use this functional view to easily describe\nevaluation mechanisms as well. Suppose an experimenter wants to compare PeerTrust\nand EigenTrust. The inputs and outputs of these algorithms are semantically different.\nTo match the input, we can use a function that discretizes continuous feedback values\n(f (a, b)) in [0, 1] to {-1, 1}, using some threshold t:\n\nTable 1 A classification for trust models\n\nStage Global or\nAbsolute or\n\nTrust Algorithm\nTransitions\n\nInput\nLocal\n\nRelative\nReputation Scores\n\nEigenTrust 0 → 2\nsatisfaction\n\nglobal relativeratings\n\nPeerTrust 0 → 2\nsatisfaction\n\nglobal absoluteratings\n\nAppleSeed 2 → 2\nreputation\n\nlocal absolutescores\n\nAberer & Despotovic 0 → 3 complaints global N/A\n\nAdvogato 3 → 3 certificates local N/A\n\nTRAVOS 0 → 2\nsatisfaction\n\nlocal absoluteratings\n\nRanking 2 → 3\nreputation\n\nN/A relatives",
      "keyphrases": [
        "computational trust models",
        "testbed",
        "experiments",
        "analysis"
      ],
      "title": "Toward a testbed for evaluating computational trust models: experiments and analysis",
      "author": "Partheeban Chandrasekaran",
      "publicationName": "Journal of Trust Management",
      "doi": "10.1186/s40493-015-0019-z",
      "publicationDate": "2015-09-07"
    }
  ]
}
```

---

### Query 6

**Description**: *Search for "artificial intelligence", where the publication name matches "information" or "data" and get the result count*

**Query string**: `search=artificial inteligence&$count=true&$filter=search.ismatch('information|data', 'publicationName')`

**Index**: library

**Results**:
```json
{
  "@odata.context": "https://corporate-training-search.search.windows.net/indexes('papers-index')/$metadata#docs(*)",
  "@odata.count": 3,
  "value": [
    {
      "@search.score": 0.95316994,
      "content": "\nMobile marketing recommendation method \nbased on user location feedback\nChunyong Yin1 , Shilei Ding1 and Jin Wang2*\n\nIntroduction\nIn recent years, the e-commerce industry has developed rapidly with the popularization \nof the Internet. At this time, famous e-commerce platforms such as Alibaba and Ama-\nzon were born. E-commerce moved physical store products to a virtual network plat-\nform. On the one hand, it is convenient for users to buy various products without leaving \nthe home. On the other hand, it is also convenient for sellers to sell their own goods \nand reduce costs. However, the various products have made it more difficult for users \nto select products. E-commerce platform can generate a large amount of user location \nfeedback data which contains a wealth of user preference information [1]. It is significant \nto predict the location of the next consumer’s consumption from these behavioral data. \nAt present, most of the recommended methods focus on the user-product binary matrix \nand directly model their binary relationships [2]. The users’ location information and \nshopping location information are considered as the third factor. In this case, you can \nonly use the limited check-in data. The users’ location feedback behavior and the timeli-\nness of behavior are often overlooked.\n\nThe mobile recommendation system takes advantage of the mobile network environ-\nment in terms of information recommendation and overcomes the disadvantages. Filter-\ning irrelevant information by predicting potential mobile user preferences and providing \n\nAbstract \n\nLocation-based mobile marketing recommendation has become one of the hot spots \nin e-commerce. The current mobile marketing recommendation system only treats \nlocation information as a recommended attribute, which weakens the role of users and \nshopping location information in the recommendation. This paper focuses on location \nfeedback data of user and proposes a location-based mobile marketing recommenda-\ntion model by convolutional neural network (LBCNN). First, the users’ location-based \nbehaviors are divided into different time windows. For each window, the extractor \nachieves users’ timing preference characteristics from different dimensions. Next, we \nuse the convolutional model in the convolutional neural network model to train a \nclassifier. The experimental results show that the model proposed in this paper is better \nthan the traditional recommendation models in the terms of accuracy rate and recall \nrate, both of which increase nearly 10%.\n\nKeywords: Location feedback, Mobile marketing, Convolutional neural network, \nSequential behavior\n\nOpen Access\n\n© The Author(s) 2019. This article is distributed under the terms of the Creative Commons Attribution 4.0 International License \n(http://creat iveco mmons .org/licen ses/by/4.0/), which permits unrestricted use, distribution, and reproduction in any medium, \nprovided you give appropriate credit to the original author(s) and the source, provide a link to the Creative Commons license, and \nindicate if changes were made.\n\nRESEARCH\n\nYin et al. Hum. Cent. Comput. Inf. Sci.            (2019) 9:14  \nhttps://doi.org/10.1186/s13673-019-0177-6\n\n*Correspondence:   \njinwang@csust.edu.cn \n2 School of Computer & \nCommunication Engineering, \nChangsha University \nof Science & Technology, \nChangsha 410004, China\nFull list of author information \nis available at the end of the \narticle\n\nhttp://orcid.org/0000-0001-5764-2432\nhttp://creativecommons.org/licenses/by/4.0/\nhttp://crossmark.crossref.org/dialog/?doi=10.1186/s13673-019-0177-6&domain=pdf\n\n\nPage 2 of 17Yin et al. Hum. Cent. Comput. Inf. Sci.            (2019) 9:14 \n\nmobile users with results that meet users’ individual needs gradually become an effec-\ntive means to alleviate “mobile information overload” [3]. Mobile users have different \npreferences in different geographical locations. For this problem, how to use location \ninformation to obtain mobile users’ preferences and provide accurate personalized \nrecommendations has become a hot topic in mobile recommendation research [4]. \nAlthough there are many researches based on location recommendation, they mainly \nfocus on service resources without positional relevance. To solve the shortcomings of \nresearch on location relevance of service resources is few [5], Zhu et  al. [6] proposed \nthe method which is based on the user’s context information to analyze the user’s pref-\nerences and retrograde. Their approach is to derive user preferences by proposing two \ndifferent assumptions and then recommending user models based on preference analy-\nsis. Yin et al. [7] proposed LA-LDA. The method is a location-aware based generation \nprobability model, which uses scoring based on location to model user information and \nrecommend to users. However, these methods only treat location information as an \nattribute without considering the spatial information of users or items and weaken loca-\ntion information’s role in the recommendation. There are some studies determine user \npreferences by the distance between the mobile user and the merchant [8], but only set \nthe area based on the proximity of the distance and ignore the spatial activities of the \nmobile user [9]. However, these methods were limited to the analysis of user informa-\ntion and product information, and did not carefully consider the importance of user and \nbusiness location information. Therefore, the user preference model based on location \nrecommendation they created has some gap.\n\nConsidering the core of mobile marketing recommendation is location movement, \nLian et al. [10] proposed an implied feature-based cognitive feature collaborative filter-\ning (ICCF) framework, which avoids the impact of negative samples by combining con-\nventional methods and semantic content. In terms of algorithms, the author proposed \nan improved algorithm that can expand according to data size and feature size. To deter-\nmine the relevance of the project to user needs, Lee et al. [11] developed context infor-\nmation analysis and collaborative filtering methods for multimedia recommendations in \nmobile environments. Nevertheless, these methods only used small-scale training data \nand could not achieve accurate prediction of long-term interest for users. In this paper, \ndeep learning and time stamps are used to compensate for these shortcomings.\n\nWith great achievements in visual and speech tasks, the Deep Learning (DL) model \nhas become a novel field of study [12]. Because of the interventional optimization of \ndeep learning algorithms, artificial intelligence has made great breakthroughs in many \naspects. It is well known that models obtained through deep learning and machine learn-\ning models have very similar effects, which learns advanced abstract features from the \noriginal input features by simulating the network structure of the human nervous sys-\ntem. Experiments show that the deep model can express the characteristics of the data \nbetter than the shallow model [13]. Weight sharing by convolution makes CNN similar \nto biological neural networks, which reduces the difficulty of network structure and the \nnumber of weights. The structure of CNN is roughly divided into two layers. It is well \nknown that the first layer is a convolutional layer. Each neuron’s input is connected to the \nprevious layer through a convolution kernel and the local features are extracted. Next \nlayer is a pooling layer. In this layer, the neurons in the network are connected through \n\n\n\nPage 3 of 17Yin et al. Hum. Cent. Comput. Inf. Sci.            (2019) 9:14 \n\na convolution kernel to extract the overall features. Convolutional neural networks have \ngreat advantages in processing two-dimensional features [14], such as images.\n\nBased on our detailed comparative analysis, this paper proposes a location-based \nmobile marketing recommendation model by convolutional neural network (LBCNN). \nFirstly, we use user-product information as a training sample, and treat this problem as \na two-class problem. The category of the problem is divided into the purchase behav-\nior and the purchase behavior of the product at the next moment. In order to capture \nthe user’s timing preference characteristics, we divide the behavior of the merchandise \naccording to a certain length of time window and dig deeper into the behavior charac-\nteristics of each time window. Secondly, we consider the users’ timing preferences and \noverall preferences for the product. Then, the features of time window are used to train \nconvolutional neural network models. Finally, we input the sample features of the test \nset into the model and generate the Top-K sample as the location-based purchase fore-\ncast results [15].\n\nRemain of the paper is divided into four sections. Related work is shown in “Related \nwork” section. Necessary definitions and specific implementation of the location-based \nmobile marketing recommendation model by convolutional neural network (LBCNN) \nare shown in “Location-based mobile marketing recommendation model by CNN” sec-\ntion. In “Experimental analysis” section, experimental analysis is introduced. “Conclu-\nsion” section summarizes the strengths and weaknesses of the paper and proposes plans \nfor future progress.\n\nRelated work\nIn the current chapter, we will review existing methods for recommending systems \nthat can be broadly divided into three parts: content filtering, collaborative filtering \nand hybrid methods. We also discuss the establishment of feature models based on \ntime series to clearly represent the differences between our research and other existing \nmethods.\n\nTraditional recommendation method\n\nIn the general products recommendation system, the similarity between users is calcu-\nlated by the user’s interest feature vector. Then, the system recommends some products \nwith similarity greater than a certain threshold or the similar Top-N products to the tar-\nget user. This is a traditional recommendation algorithm based on content and the rec-\nommendation is based on comparing users.\n\na. Content‑based recommendation method\n\nContent-based information filtering has proven to be an effective application for \nlocating text documents related to topics. In particular, we need to focus on the \napplication of content-based information filtering in the recommendation system. \nContent-based methods allow for accurate comparisons between different texts \nor projects, so the recommended results are similar to the historical content of the \nuser’s consumption. The content-based recommendation algorithm involves the fol-\nlowing aspects. User description file describes the user’s preferences, which can be \nfilled by the user and dynamically updated based on the user’s feedback information \n\n\n\nPage 4 of 17Yin et al. Hum. Cent. Comput. Inf. Sci.            (2019) 9:14 \n\n(purchasing, reading, clicking, etc.) during the operation of the system. The project \nprofile describes the content characteristics of each project, which constitutes the \nfeature vector of the project. In addition, the similarity calculation is the similarity \nbetween the user’s description file and the item feature vector.\n\nThe similarity calculation of the content-based recommendation algorithm usually \nadopts the cosine similarity algorithm. The algorithm needs to calculate the similarity \nbetween the feature vector of user u and the feature vector of item i. The calculation \nformula is as shown in Formula (1).\n\nwhere ⇀u denotes the user feature vector, \n⇀\n\ni  denotes the project feature vector, \n⇀\n\n|u| is the \nmodulus of the user feature vector and \n\n⇀\n\n|i| is the model of the project feature vector.\nRepresentative content-based recommendation systems mainly include Lops, \n\nGemmis, and Semeraro [16]. Compared to other methods, content-based recom-\nmendations have no cold-start issues and recommendations are easy to understand. \nHowever, the content filtering based recommendation method has various draw-\nbacks, such as strongly relying on the availability of content and ignoring the context \ninformation of the recommended party. The content-based recommendation method \nalso has certain requirements for the format of the project. Besides, it is difficult to \ndistinguish the merits of the project. The same type of project may have the same type \nof features, which are difficult to reflect the quality of the project.\n\nb. Collaborative filtering method\n\nThe recommendation based on collaborative filtering solves the recommendation \nproblem by using the information of similar users in the same partition to analyze and \nrecommend new content that has not been scored or seen by the target user.\n\nRegarding the traditional collaborative filtering method based on memory, we \nunderstand that this method is based on the different relationships between users and \nprojects. According to expert research, the traditional collaborative filtering method \nbased on memory should be divided into the following three steps.\n\nStep 1: collection of user behavior data, this step represents the user’s past behav-\nior with a m * n matrix R. The matrix  Umn represents the feedback that the user m \nhas on the recommended object n. Rating is a range of values and different values \nrepresent how much the user likes the recommended object.\n\nStep 2: establishment of a user neighbor: establish mutual user relationships by \nanalyzing all user historical behavior data.\n\n(1)sim(u, i) =\n\n⇀\nu ·\n\n⇀\n\ni\n\n⇀\n\n|u|\n⇀\n\n|i|\n\nU =\n\n\n\n\n\n\n\nU11 U12 . . . U1n\n\nU21 U22 . . . U2n\n\n. . . . . . . . . . . .\n\nUm1 Um2 . . . Umn\n\n\n\n\n\n\n.\n\n\n\nPage 5 of 17Yin et al. Hum. Cent. Comput. Inf. Sci.            (2019) 9:14 \n\nStep 3: generate recommendation results: find the most likely N objects from the rec-\nommended items selected by similar user sets.\n\nTherefore, recommendations are made by mining common features in similar users’ pref-\nerence information [17]. The normal methods in this classification include k-nearest neigh-\nbor (k-NN), matrix decomposition, and semi-supervised learning. According to the survey, \nAmazon uses an item-by-item collaborative filtering method to recommend personalized \nonline stores for each customer.\n\nCompared to other method, collaborative filtering has the ability to filter out informa-\ntion that can be automatically recognized by the machine and effectively use feedback from \nother similar users. However, collaborative filtering requires more ratings for the project, \nso it is affected by the issue of rating sparsity. In addition, this method does not provide a \nstandard recommendation for new users and new projects, which is called a cold start issue.\n\nc. Hybrid recommendation method\n\nThe hybrid recommendation method combines the above techniques in different ways to \nimprove the recommended performance and optimize the shortcomings of the conven-\ntional method. Projects that cannot be recommended for collaborative filtering are gener-\nally addressed by combining them with content-based filtering [18].\n\nThe core of this method is to independently calculate the recommendation results of the \ntwo types of recommendation algorithms, and then mix the results. There are two specific \nhybrid methods. One method is to mix the predicted scores of the two algorithms linearly. \nAnother hybrid method is to set up an evaluation standard, compare the recommended \nresults of the two algorithms, and take the recommendation results of the higher evaluation \nalgorithms. In general, the hybrid recommendation achieves a certain degree of compensa-\ntion between different recommendation algorithms. However, the hybrid recommendation \nalgorithm still needs improvement in complexity.\n\nd. Recommendation based on association rules\n\nThe association rule algorithm is a traditional data mining method that has been widely \nused in business for many years. The core idea is to analyze the rules of user historical \nbehavior data to recommend more similar behavioral items [19]. Rules can be either user-\ndefined or dynamically generated by using rule algorithms. The effect of the algorithm \ndepends mainly on the quantity and quality of the rules so the focus of the algorithm is on \nhow to develop high quality rules.\n\nDefine N as the total number of transactions, R is the total project and U and V are two \ndisjoint sets of items (U∩V ≠ ∅, U∈R, V∈R). The association rule is essentially an IF–Then \nstatement, here is expressed by U → V. The strength of the association rule U → V can be \nmeasured by two criteria: support and confidence. S is the ratio containing U and V data \nwhich both represent the number of transactions, which is shown in Formula (2).\n\nC is the ratio of U, V data to the only U data which represents the number of transac-\ntions, as shown in Formula (3)\n\n(2)S(U → V ) =\nN (U ∪ V )\n\nN\n.\n\n\n\nPage 6 of 17Yin et al. Hum. Cent. Comput. Inf. Sci.            (2019) 9:14 \n\nThe recommendation process of the algorithm is shown in below.\nFirstly, according to the items of interest to the user, the user’s interest in other \n\nunknown items is predicted by rules. Secondly, compare the support of the rules. Finally, \nthe recommended items of TOP-N are obtained to the user.\n\nThe recommendation system based on association rules includes three parts: the key-\nword, the presentation and the user interface. The keyword layer is a set of keyword \nattributes and dependencies between keywords. The description layer connects the \nkeyword layer and the user layer and the main function is to describe the user and the \nresource. The user interface layer is the layer that interacts directly with the user. How-\never, the system becomes more and more difficult to manage as the rules increasing. In \naddition, there is a strong dependence on the quality of the rules and a cold start prob-\nlem is existed.\n\nMost of the recommendation systems use collaborative filtering algorithm to recom-\nmend for users. However, the traditional algorithm can only analyze ready-made data \nsimply, and most systems simply preprocess the data. In our method, we preprocess the \ndataset by extending the time information of the data to a time label. The next section is \nan explanation of the specific implementation.\n\nConstruction of time series behavior’s preference features\n\nThe timing recommendation model is based primarily on the Markov chain. This model \nmakes full use of timing behavior data to predict the next purchase behavior based on \nthe user’s last behavior. The advantage of this model is that it can generate good recom-\nmendations by timing behavior.\n\nAs shown in Fig. 1, the prediction problem of product purchase can be expressed as \npredicts the user’s purchase behavior at time T by a user behavior record set D before \ntime T [20]. Different actions occur at different times. For example, user1 visit location \na and b when user1 purchasing b and c at T − 3. We need to predict T-time consumer \nbehavior based on different timing behavior characteristics.\n\nAccording to relevant professional research, we divide the data sets of user behav-\nior into three groups in a pre-processing manner. By the feature statistics method, the \n\n(3)C(U → V ) =\nN (U ∪ V )\n\nN\n.\n\nFig. 1 The time series of user position feedback\n\n\n\nPage 7 of 17Yin et al. Hum. Cent. Comput. Inf. Sci.            (2019) 9:14 \n\nfeatures are divided into two types, as shown in Table 1. “True” indicates that the feature \ngroup has corresponding features. Conversely, “False” means no such feature. Next we \nexplain these features.\n\na. Counting feature\n\nFor each feature statistics window, we use the behavioral counting feature and the de-\nduplication counting feature. The behavior count is a cumulative measure of the num-\nber of behaviors that occurred in and before the current window. For the location visit \nbehavior, it represents the number of visits to the product location by the user, the total \nnumber of visits by the user and the total number of visits to the merchandise. The de-\nduplication count feature is similar to the behavioral count, but only the number of non-\nrepetitive behavioral data is counted.\n\nb. Mean feature\n\nIn order to describe the activity of the user and the popularity of the product better, \nthis article derives a series of mean-type features based on the counting features. Take \nthe location visit behavior as an example, the user characteristics group includes the \nuser’s average number of visiting to the product. The average number of visiting to \nthe product by user i is calculated as shown in Formula (4).\n\nc. Ratio feature\n\nThe ratio of user-product behavior to the total behavior of the user and the product \nis also an aspect affecting the user’s degree of preference for the product. In the time \nwindow t, the method to calculate the ratio of the user’s visit to the products’ total \nvisit is shown in Formula (5).\n\nOur work presents a mobile marketing recommendation model is trained by adding \nthe time axis to the user position features. Contrary to current research, it is highly \nusable and low difficulty of achievement for real-world work applications. Consider-\ning the speed of calculation, we study the method of directly embedding time series \ninformation into the collaborative filtering calculation process to improve the recom-\nmendation quality. Specific information will be covered in the following sections.\n\n(4)avgui(t, i, visit) =\naction_count(t,U ,Ui, visit)\n\nuser_unique_item(t,U ,Ui, visit)\n.\n\n(5)rate_ui_in_u(t, i, j, visit) =\naction_count(t,UI ,Ui, Ij, visit)\n\naction_count(t,U ,Ui, visit)\n.\n\nTable 1 Characteristic system diagram (True/False)\n\nFeature group Counting feature Mean feature Ratio feature\n\nUser-product True False True\n\nUser feature True True False\n\nProduct feature True True False\n\n\n\nPage 8 of 17Yin et al. Hum. Cent. Comput. Inf. Sci.            (2019) 9:14 \n\nLocation‑based mobile marketing recommendation model by CNN\nCreating the model is one of the most important aspects, which is an evaluation crite-\nrion to make sure correctness of the next step. This section mainly describes the rel-\nevant definitions of LBCNN that are shown in “Relevant definitions of the LBCNN” \nsection, and specific implementation of the model is shown in “Specific implementa-\ntion of the model” section.\n\nRelevant definitions of the LBCNN\n\nIn order to get better feature expression, we consider the user’s timing sensitivity of the \nproduct preferences and the user’s overall preferences comprehensively. This paper uses a \nconvolutional neural network as the basis to build location-based mobile marketing recom-\nmendation model. In the next step, we give the relevant definition.\n\na. Definition 1 (Model framework): based on the above analysis and user’s timing behav-\nior preference feature. We use the convolutional neural network model shown in Fig. 2. The \nmodel is divided into four layers that are input layer, multi-window convolution layer, pool-\ning layer and output layer. The input layer is a well-constructed input feature which trans-\nforms the input features into a two-dimensional plane by time series. Each time window is \nexpressed as an eigenvector. The multi-window convolutional layer convolves the input fea-\nture plane through different lengths of time windows to obtain different feature maps. The \npooling layer reduces the dimension of the feature map to obtain a pooled feature vector. \nThe output layer and the pooling layer are fully connected network structures.\n\nb. Definition 2 (Convolution layer): assume that there are N time windows of the feature \nand each time window has K user preference feature for the commodity. Then input sam-\nple × can be expressed as a matrix of T × K. The feature map in the convolutional layer is \ncalculated by the input layer and the convolution kernel. The window length of the convolu-\ntion kernel is h. xi,i+j represents the eigenvector added by time window i and time window \ni + j. The convolution kernel w can be expressed as a vector of h × K. Feature map f = [f1, f2, \n…, fT−h+1]. The i-th feature fi is calculated according to Formula (6):\n\n(6)fi = σ(w · xi,i+h−1 + b)\n\nFig. 2 The framework of the LBCNN\n\n\n\nPage 9 of 17Yin et al. Hum. Cent. Comput. Inf. Sci.            (2019) 9:14 \n\nwhere b is an offset term and a real number. σ(x) is a nonlinear activation function. This \npaper uses ReLu and Tanh as an activation function. Relu is shown in Formula (7):\n\nc. Definition 3 (Max-pooling): the pooling layer is to scale the feature map while reduc-\ning the complexity of the network. The maximum features of the convolution kernel can \nbe obtained according to the maximum pooling operation. The feature map obtained \nat the kth product of the convolutional kernel is fk = [fk,1, fk,2, …, fk,T−h +1]. The pooling \noperation can be expressed as Formula (8):\n\nd. Definition 4 (Probability distribution): there are M convolution kernels and the output \nlayer has C categories [19]. The weight parameter θ of the output layer is a C × M matrix. \nThe pooled feature f̂  of x is an M-dimensional vector. The probability that x belongs to \nthe i-th category can be expressed as Formula (9):\n\nwhere  bk represents the k-th offset of the fully connected layer. The loss function of the \nmodel can be obtained by the likelihood probability value, as shown in Formula (10):\n\nwhere T is the training data set,  yi is the real category of the i-th sample, xi is the charac-\nteristic of the i-th sample and θ is the model’s parameters. We learn model parameters \nby minimizing the loss function. The training method adopts the improved gradient \ndescent method proposed by Zeiler. In addition, we have adopted Dropout process-\ning on the convolutional layer to prevent over-fitting of the trained model [21]. The \nDropout method randomizes the neurons in the convolutional layer to 0 with a certain \nprobability.\n\ne. Definition 5 (Latent factor): the value of the latent factor vector is true [22]. Whether \nan item belongs to a class is determined entirely by the user’s behavior. We assume that \ntwo items are liked by many users at the same time, then these two items have a high \nprobability of belonging to the same class. The weight of an item in a class can also be \ncalculated by itself. The implicit semantic model calculates the user’s (u) interest in the \nitem (i) are shown in Formula (11):\n\n(7)\nReLu = max(0, x).\n\nTanh(x) =\nex − e−x\n\nex + e−x\n.\n\n(8)Pool_feature(j) = down(fi).\n\n(9)p(i|x, θ) =\ne(θi·\n\n⌢\nf +bi)\n\n∑C\nk−1 e\n\n(θk ·\n⌢\nf +bk )\n\n(10)J (θ) = −\n\nk\n∑\n\ni=1\n\nlog(p(yi|x, θ))\n\n(11)R(u, i) = rui = pTu qi =\n\nF\n∑\n\nf=1\n\npu,kqi,k\n\n\n\nPage 10 of 17Yin et al. Hum. Cent. Comput. Inf. Sci.            (2019) 9:14 \n\nwhere p is the relationship between the user interest and the kth implicit class. q is the \nrelationship between the kth implicit class and the item i. F is the number of hidden \nclasses, and r is the user’s interest in the item.\n\nSpecific implementation of the model\n\nWe can draw from Fig. 3 that the proposed model is divided into two processes. The first \nprocess is the training process and includes two parts. The top module shows how to gener-\nate CNN inputs and outputs from historical data. The other module in the training process \nshows that the traditional CNN parameters are trained by provided data. The second pro-\ncess finished a new location-based marketing resources recommendation. The recommen-\ndation process can work through the CNN parameters provided by the training process.\n\nTo achieve the features of users and location-based mobile marketing resources, the \nlatent factor model (LFM) is used. In traditional LFM, L2-norm regularization is often used \nto optimize training results. However, using L2-norm regularization often leads to excessive \nsmoothing problems. In our model, LFM results are used to represent the characteristics of \nthe training data. In this kind of thinking, we can learn from the training method of regres-\nsion coefficient in regression analysis, and construct a loss function. Therefore, it is more \nreasonable to use sparseness before the specification results. Based on these analyses, we \npropose an improved matrix decomposition method and try to normalize the solution by \n\nFig. 3 Location-based mobile marketing recommendation model by convolutional neural network\n\n\n\nPage 11 of 17Yin et al. Hum. Cent. Comput. Inf. Sci.            (2019) 9:14 \n\nusing the premise of verifying the sparseness of the matrix. The model is presented as For-\nmula (12):\n\nThe next question is how to calculate these two parameters p and q. For the calculation \nof this linear model, this paper uses the gradient descent method. In the Formula (12), \n puk is a user bias item that represents the average of a user’s rating.  qik is an item offset \nitem that represents the average of an item being scored. The offset term is an intrinsic \nproperty that indicates whether the item is popular with the public or a user is harsh \non the item. For positive samples, we specify  ru,i = 1 based on experience and negative \nsample  ru,i = 0, which is shown in Formula (11). The latter λ is a regularization term to \nprevent overfitting.\n\na. Description of the training section\n\nIn Fig. 3, If you want to train CNN, the first thing you need to solve is its input and out-\nput problems. For input, a language model is usually used.\n\nIn terms of output, we propose an improvement in model training by LFM, which is \nconstrained by the regularization of the L1-norm [23]. LFM training data is a historical \nscore between the user and the location-based marketing resources. The rating score can \nbe explicit because it is based on a user tag or an implied tag and it is predicted from the \nuser’s behavior. In this model, in order to ensure that the trained model is representative, \nthe training data we input is to select the existing authoritative standard training set.\n\nb. Description of the recommended part\n\nOnce the LBCNN model structure is established and the model parameters are trained \nusing the training data set, the recommended real-time performance can be achieved. \nThe real-time performance is based on the update of network model parameters in the \nbackground, and it uses some past behavior data and information of the recommended \npeople and products.\n\nUser information and product information can be obtained in advance and digitized. \nIn the offline training model phase, digitized user information, product information, and \nbehavior information are utilized [24]. The same model is trained for the same type of \nusers, and the parameters of the model are periodically updated within a certain period \nof time. In the real-time recommendation stage, real-time recommendation can be real-\nized only by integrating the collected behavior data with the previous data and inputting \nit into the model.\n\nExperimental analysis\nIn order to verify the advantages of convolutional neural network in capturing user’s \ntiming preferences for product and mining users’ temporal behavior characteristics, \nwe compare several commonly used classification models under the same conditions of \ntraining features. They are Linear Logistic Regression Classification Model (LR), Support \n\n(12)J (U ,V ) =\n∑\n\nu,i∈K\n\n(\n\nru,i −\n\nk\n∑\n\nk=1\n\npu,kqi,k\n\n)2\n\n+ ��puk�\n2 + ��qik�\n\n2.\n\n\n\nPage 12 of 17Yin et al. Hum. Cent. Comput. Inf. Sci.            (2019) 9:14 \n\nVector Machine (SVM), Random Forest Model (RF) and Gradient Boosting Regression \nTree Model (GBDT) [25]. We also compare the products that have been visited for the \nlast 8 h. Experimental tool is sklearn kit. The hyper parameter settings for each model \nduring the experiment are:\n\na. LR: select L2 regular and the regularization coefficient is 0.1.\nb. SVM: choose radial basis kernel function (RBF) and gamma of kernel function is \n\n0.005.\nc. RF: the number of trees is 200, the entropy is selected as the feature segmentation \n\nstandard and the random feature ratio is 0.5.\nd. GBDT: the number of trees is 100, the learning rate is 0.1 and the maximum depth of \n\nthe tree is 3.\n\nDescription of the data set\n\nThe experiment in our paper uses the dataset disclosed according to the Alibaba Group’s \nmobile recommendation algorithm contest held in 2015. This data set contains 1 month \nof user behavior data and product information. The user’s behavior data includes 10 mil-\nlion users’ various behaviors on 2,876,947 items. Behavior types include clicks, shopping \ncarts and purchases. In addition, each behavior record identifies behavior time that is \naccurate to the hour. The product information includes product category information, \nand identifies whether the product is an online to offline type. In a real business sce-\nnario, we often need to build a personalized recommendation model for a subset of all \nproducts. In the",
      "metadata_storage_path": "aHR0cHM6Ly9jb3Jwb3JhdGV0cmFpbmRhdGEuYmxvYi5jb3JlLndpbmRvd3MubmV0L3BhcGVycy9zMTM2NzMtMDE5LTAxNzctNi5wZGY1",
      "keyphrases": [
        "Mobile marketing recommendation method",
        "user location feedback"
      ],
      "title": "Mobile marketing recommendation method based on user location feedback",
      "author": "Chunyong Yin ",
      "publicationName": "Human-centric Computing and Information Sciences",
      "publisher": "Springer",
      "doi": "10.1186/s13673-019-0177-6",
      "publicationDate": "2019-05-01"
    },
    {
      "@search.score": 0.95316994,
      "content": "\nImproving prediction with enhanced \nDistributed Memory‑based Resilient Dataset \nFilter\nSandhya Narayanan1*, Philip Samuel2 and Mariamma Chacko3\n\nIntroduction\nAnalyzing and processing massive volumes of data in different applications like sensor \ndata, health care and e-Commerce require big data processing technologies. Extracting \nuseful information from the enormous size of unstructured data is a crucial thing. As the \namount of data becomes more extensive, sophisticated pre-processing techniques are \nrequired to analyze the data. In social networking sites and other online shopping sites, \na massive volume of online product reviews from a large size of customers are available \n[1]. The impact of online product reviews affects 90% of the current e-Commerce mar-\nket [2]. Customer reviews contribute the product sale to an extent and product life in the \nmarket depends on online product recommendations.\n\nOnline feedback is one of the communication methods which gives direct suggestions \nfrom the customers [3, 4]. Online reviews and ratings from customers are another infor-\nmation source about product quality [5, 6]. Customer reviews can help to decide on a new \nsuccessful product launch. Online shopping has several advantages over retail shopping. In \nretail shopping, the customers visit the shop and receive price information but less product \n\nAbstract \n\nLaunching new products in the consumer electronics market is challenging. Develop-\ning and marketing the same in limited time affect the sustainability of such companies. \nThis research work introduces a model that can predict the success of a product. A \nFeature Information Gain (FIG) measure is used for significant feature identification \nand Distributed Memory-based Resilient Dataset Filter (DMRDF) is used to eliminate \nduplicate reviews, which in turn improves the reliability of the product reviews. The \npre-processed dataset is used for prediction of product pre-launch in the market using \nclassifiers such as Logistic regression and Support vector machine. DMRDF method is \nfault-tolerant because of its resilience property and also reduces the dataset redun-\ndancy; hence, it increases the prediction accuracy of the model. The proposed model \nworks in a distributed environment to handle a massive volume of the dataset and \ntherefore, it is scalable. The output of this feature modelling and prediction allows the \nmanufacturer to optimize the design of his new product.\n\nKeywords: Distributed Memory-based, Resilient Distribution Dataset, Redundancy\n\nOpen Access\n\n© The Author(s) 2020. This article is licensed under a Creative Commons Attribution 4.0 International License, which permits use, sharing, \nadaptation, distribution and reproduction in any medium or format, as long as you give appropriate credit to the original author(s) and \nthe source, provide a link to the Creative Commons licence, and indicate if changes were made. The images or other third party material \nin this article are included in the article’s Creative Commons licence, unless indicated otherwise in a credit line to the material. If material \nis not included in the article’s Creative Commons licence and your intended use is not permitted by statutory regulation or exceeds the \npermitted use, you will need to obtain permission directly from the copyright holder. To view a copy of this licence, visit http://creat iveco \nmmons .org/licen ses/by/4.0/.\n\nRESEARCH\n\nNarayanan et al. J Big Data            (2020) 7:13  \nhttps://doi.org/10.1186/s40537‑020‑00292‑y\n\n*Correspondence:   \nnairsands@gmail.com \n1 Information Technology, \nSchool of Engineering, \nCochin University of Science \n& Technology, Kochi 682022, \nIndia\nFull list of author information \nis available at the end of the \narticle\n\nhttp://creativecommons.org/licenses/by/4.0/\nhttp://creativecommons.org/licenses/by/4.0/\nhttp://crossmark.crossref.org/dialog/?doi=10.1186/s40537-020-00292-y&domain=pdf\n\n\nPage 2 of 15Narayanan et al. J Big Data            (2020) 7:13 \n\ninformation from shop owners. On the other hand, online shopping sites give product \nreviews and previous customer feedbacks without extra cost and effort for the customers \n[7–10].\n\nInvesting in poor quality products potentially affects an industry’s brand loyalty and this \nstrategy should be changed by the eCommerce firms [5, 11]. Consumer product success \ndepends on different criteria, such as the quality of the product and marketing strategies. \nThe users should provide their valuable and accurate reviews about the products [12]. Cus-\ntomers bother to give reviews about products, whether they liked it or not. If the users \nprovide reviews, then other retailers can create some duplicated reviews [13, 14]. In online \nmarketing, the volume and value of product reviews are examined [15, 16]. The number \nof the product reviews on the shopping sites, blogs and forums has increased awareness \namong the users. This large volume of the reviews leads to the need for significant data \nprocessing methods [17, 18]. The value is the rating on the products. The ratio of positive to \nnegative reviews about the product leads to the quality of the product [19, 20].\n\nFeature selection is a crucial phase in data pre-processing [21]. Selecting features from \nan un-structured massive volume of data reduce the model complexity and improves the \nprediction accuracy. Different feature selection methods existing are the filter, wrapper and \nembedded. The wrapper feature selection method evaluates the usefulness of the feature \nand it depends on the performance of the classifier [22]. The filter method calculates the \nrelevance of the features and analyzes data in a univariate manner. The embedded process \nis similar to the wrapper method. Embedded and wrapper methods are more expensive \ncompared to the filter method. The state-of-art methods in customer review analysis gener-\nally discuss on categorizing positive and negative reviews using different natural language \nprocessing techniques and spam reviews recognition [23]. Feature selection of customer \nreviews increases prediction accuracy, thereby improves the model performance.\n\nAn enhanced method, which is a combination of filter and wrapper method is proposed \nin this work, which focuses on product pre-launch prediction with enhanced distributive \nfeature selection method. Since many redundant reviews are available on the web in large \nvolumes, a big data processing model has been implemented to filter out duplicated and \nunreliable data from customer reviews in-order to increase prediction accuracy. A scalable \nbig data processing model has been applied to predict the success or failure of a new prod-\nuct. The realization of the model has been done by Distributed Memory-based Resilient \nDataset Filter with prediction classifiers.\n\nThis paper is organized as follows. “Related work” section discusses related work. “Meth-\nodology” section contains the proposed methodology with System design, Resilient Distrib-\nuted Dataset and Prediction using classifiers. “Results and discussions” section summarizes \nresults and discussion. The conclusion of the paper is shown in “Conclusion and future \nwork” section.\n\nRelated work\nMakridakis et al. [24] illustrate that machine learning methods are alternative methods \nfor statistical analysis of multiple forecasting field. Author claims that statistical methods \nare more accurate than machine learning [25] methods. The reason for less accuracy is \nthe unknown values of data i.e., improper knowledge and pre-processing of data.\n\n\n\nPage 3 of 15Narayanan et al. J Big Data            (2020) 7:13  \n\nDifferent works have been implemented using the Matrix factorization (MF) [14] \nmethod with collaborative filtering [26]. Hao et al. [15] focused on a work based on the \nfactorization of the user rating matrix into two vectors, i.e., user latent and item latent \nwith low dimensionality. The sum of squared distance can be minimized by training a \nmodel that can find a solution using Stochastic Gradient Decent [27] or by least squares \n[28]. Salakhutdinov et al. [29] proposed a method that can be scaled linearly by probabil-\nity related matrix factorization on a big volume of datasets and then comparing it with \nthe single value decomposition method. This matrix factorization outperforms other \nprobability factorization methods like Bayesian-based probabilistic analysis [29] and \nstandard probability-based matrix factorization methods. A conventional approach, like \ntraditional collaborative Filtering [13, 30] method depends on customers and items. The \nuser item matrix factorization technique has been used for implementation purpose. \nIn the recommender system, there is a limitation in the sparsity problem and cold start \nproblem. In addition to the user item matrix factorization method, various analyses and \napproaches have been implemented to solve these recommendation issues.\n\nWietsma et al. [31] proposed a recommender system that gives information about the \nmobile decision aid and filtering function. This has been implemented with a study of \n29 features of student user behavior. The result shows the correlation among the user \nreviews and product reviews from different websites. Jianguo Chen et al. [32] proposed \na recommendation system for the treatment and diagnosis of the diseases. For cluster \nanalysis of disease symptoms, a density-peaked method is adopted. A rule-based apriori \nalgorithm is used for the diagnosis of disease and treatment. Asha et al. [33] proposed \nthe Gini-index feature method using movie review dataset. The sentimental analysis \nof the reviews are performed and opinion extraction of the sentences are done. Gini-\nindex impurity measure improves the accuracy of the polarity prediction by sentimental \nanalysis using Support vector machine [34, 35]. Depending on the frequency of occur-\nrence of a word in the document, the term frequency is calculated and opinion words \nare extracted using the Gini-index method. In this method, high term frequency words \nare not included, as it decreases the precision. The disadvantage of this method is that \nfor the huge volume of data, the prediction accuracy decreases.\n\nLuo et al. [36] proposed a method based on historical data to analyze the quality of \nservice for automatic service selection. Liu et al. [37] proposed a system in a mobile envi-\nronment for movie rating and review summarization. The authors used Latent Semantic \nAnalysis (LSA-based) method for product feature identification and feature-based sum-\nmarization. Statistical methods [38] have been used for identifying opinion words. The \ndisadvantage of this method is that LSA-based method cannot be represented efficiently; \nhence, it is difficult to index based on individual dimensions. This reduces the prediction \naccuracy in large datasets.\n\nLack of appropriate computing models for handling huge volume and redundancy in \ncustomer review datasets is a major challenge. Another major challenge handled in the \nproposed work is the existence of a pre-launch product in the industry based on the \nproduct features, which can be predicted based on the customer feedback in the form \nof reviews and ratings of the existing products. This prediction helps to optimize the \ndesign of the product to improve its quality with the required product features. Many \nof the relational database management systems are handling structured data, which is \n\n\n\nPage 4 of 15Narayanan et al. J Big Data            (2020) 7:13 \n\nnot scalable for big data that handles a large volume of unstructured data. This proposed \nmodel solves the problem of redundancy in a huge volume of the dataset for better pre-\ndiction accuracy.\n\nMethodology\nA pre-launch product prediction using different classifiers has been analysed by huge \ncustomer review and rating dataset. The product prediction is done through the phases \nconsisting of data collection phase, feature selection and duplicate data removal, build-\ning prediction classifier, training as well as testing.\n\nFigure 1 describes the various stages in system design of the model. The input dataset \nconsists of multivariate data which includes categorical, real and text data. Input dataset \nis fed for data pre-processing. Data pre-processing consists of feature selection, redun-\ndancy elimination and data integration which is done using Feature Information Gain \nand Distributed Memory-based Resilient Dataset Filter approach. The cleaned dataset \nis trained using classification algorithms. The classifiers considered for training are Sup-\nport Vector Machine (SVM) and Logistic Regression (LR). Further the dataset is tested \nfor pre-launch prediction using LR and SVM.\n\nData collection phase\n\nThis methodology can be applied for different products. Several datasets like Ama-\nzon and flip cart customer reviews are available as public datasets [39–41]. The data-\nset of customer reviews and ratings of seven brands of mobile phones for a period of \n24 months are considered in this work. The mobile phones product reviews are chosen \nbecause of two reasons. New mobile phones are launched into the market industry day \nby day which is one of the unavoidable items in everyone’s life. Market sustainability for \nthe mobile phones is very low.\n\nTable  1 shows a sample set of product reviews in which input dataset consists of \nuser features and product features. User features consists of Author, ReviewID and \nTitle depending on the user. Product feature consists of Product categories, Overall \nratings and Review Content. Since mobile phone is taken as the product, the catego-\nrization is done according to the features such as Battery life, price, camera, RAM, \n\nData collection \n\nCategorical\n\nText\n\nReal\n\nData Pre-\nprocessing\n\nFeature \nIdentification\n\nRedundancy\nRemoval\n\nData \nIntegration\n\nTraining \nDataset Using \nclassification \nalgorithms\n\nSupport \nVector \n\nLogistic \nRegression\n\nTesting Dataset \nUsing \n\nclassification \nalgorithms\n\nLogistic \nRegression\n\nSupport \nVector \n\nFig. 1 Product prelaunch prediction System Design\n\n\n\nPage 5 of 15Narayanan et al. J Big Data            (2020) 7:13  \n\nprocessor, weight etc. Some features are given a priority weightage depending on the \nproduct and user requirements. Input dataset with JSON file format is taken.\n\nDataset pre‑processing\n\nIn data pre-processing, feature selection plays a major role. In the product review \ndataset of a mobile phone, a large number of features exist. Identifying a feature from \ncustomer reviews is important for this model to improve the prediction accuracy. \nEnhanced Feature Information Gain measure has been implemented to identify sig-\nnificant feature.\n\nFeatures are identified based on the content of the product reviews, ratings of the \nproduct reviews and opinion identification of the reviews. Ratings of the product \nreviews can be further categorized based on a rating scale of 5 (1—Bad, 2—Average, \n3—Good, 4—very good, 5—Excellent). For opinion identification of the product, the \npolarity of extracted opinions for each review is classified using Senti-WordNet [42].\n\nFeature Information Gain measures the amount of information of a feature \nretrieved from a particular review. Impurity which is the measure of reliability of fea-\ntures in the input dataset should be reduced to get significant features. To measure \nfeature impurity, the best information of a feature obtained from each review is calcu-\nlated as follows\n\n• Let Pi be the probability of any feature instance \n(\n\nf\n)\n\n of k feature set F =\n{\n\nf1, f2, . . . fk\n}\n\n \nbelonging to  ith customer review Ri , where i varies from 1 to N.\n\n• Let N denotes the total number of customer reviews.\n• Let OR denotes the polarity of extracted opinions of the Review.\n• Let SR denotes product rating scale of review (R).\n\nTable 1 Sample set of Product Reviews\n\n\n\nPage 6 of 15Narayanan et al. J Big Data            (2020) 7:13 \n\nThe information of a feature with respect to review rating and opinion is denoted by \nIf\n\nExpected information gain of the feature denoted as Ef\n\nReview Feature Impurity R(I) is calculated as\n\nThen Feature Information Gain (�G) to find out significant features are calculated \nas\n\nFeatures are selected based on the �G value and those with an Information gain \ngreater than 0.5 is selected as a significant feature. Table 2 shows the significant fea-\nture from customer reviews and ratings.\n\nNext step is to eliminate the redundant reviews and to replace null values of an \nactive customer from the customer review dataset using an enhanced big data pro-\ncessing approach. Reviews with significant features obtained from feature identifica-\ntion are considered for further processing.\n\n(1)If = log2\n\n(\n\n1\n\nP(R = F)\n\n)\n\n∗ OR ∗ SR.\n\n(2)Ef =\n\nN\n∑\n\ni=1\n\n−Pi(R = F).\n∥\n\n∥If\n∥\n\n∥\n\n1\n.\n\n(3)R(I) = −\n\nN\n∑\n\ni=1\n\nPi.log2Ef .\n\n(4)�G = R(I)−\n\nN\n∑\n\ni=1\n\n[(\n\nOR\n\nN\n∗ Ef\n\n)\n\n−\n\n(\n\nSR\n\nN\n∗ Ef\n\n)]\n\n.\n\nTable 2 Significant Features from Customer Reviews and Ratings\n\nNo Customer reviewed features No Customer reviewed features\n\n1 Author 17 RAM\n\n2 Title 18 Sim type\n\n3 ReviewID 19 Product category\n\n4 Content 20 Thickness\n\n5 Product brand 21 Weight of mobile phone\n\n6 Ratings 22 Height\n\n7 Battery life 23 Product type\n\n8 Price 24 Product rating\n\n9 Feature information gain 25 Front camera\n\n10 Review type 26 Back camera\n\n11 Product display 27 Opinion of review\n\n12 Processor 28 Multi-band\n\n13 Operating system 29 Network support\n\n14 Water proof 30 Quick charging\n\n15 Rear camera 31 Finger sensor\n\n16 Applications inbuilt 32 Internal storage\n\n\n\nPage 7 of 15Narayanan et al. J Big Data            (2020) 7:13  \n\nResilient Distributed Dataset\n\nResilient Distributed Dataset (RDD) [43] is a big data processing approach, which allows \nto store cache chunks of data on memory and persevere it as per the requirements. \nThe in-memory data caching is supported by RDD. Variety of jobs at a point of time \nis another challenge which is handled by RDD. This method deals with chunks of data \nduring processing and analysis. RDD can also be used for machine learning supported \nsystems as well as in big data processing and analysis, which happens to be an almost \npervasive requirement in the industry.\n\nIn the proposed method the main actions of RDD are:\n\n• Reduce (β): Combine all the elements of the dataset using the function β.\n• First (): This function will return the first element\n• takeOrdered(n): RDD is returned with first ‘n’ elements.\n• saveAsSequenceFile(path): the elements in the dataset to be written to the local file \n\nsystem with given path.\n\nThe main Transformations of RDD are:\n\n• map(β): Elements from the input file is mapped and new dataset is returned through \nfunction β.\n\n• filter(β): New dataset is returned if the function β returns true.\n• groupBykey(): When called a dataset of (key, value) pairs, this function returns a \n\ndataset of (key, value) pairs.\n• ReduceBykey(β): A (key, value) pair dataset is returned, where the values of each key \n\nare combined using the given reduce function β.\n\nIn the proposed work an enhanced Distributed Memory-based Resilience Dataset \nFilter (DMRDF) is applied. DMRDF method have long Lineage and it is recomputed \nthemselves using prior information, thus it achieves fault-tolerance. DMRDF has been \nimplemented to remove the redundancy in the dataset for product pre-launch predic-\ntion. This enhanced method is simple and fast.\n\n• Let the list of n customers represented as C = {c1, c2, c3 . . . , cn}\n\n• Let the list of N reviews be represented as R = {r1, r2, r3 . . . , rN }\n\n• Let x significant features are identified from feature set (F  ) represented as Fx ⊂ F\n\n• An active customer consists of significant feature having information Gain value \ndenoted by �G\n\nIn the DMRDF method, a product is chosen and its customer reviews are found out. \nEliminate customers with similar reviews on the selected product and also reviews \nwith insignificant features. Calculate the memory-based Resilient Dataset Filter score \nbetween each of the customer reviews with significant features.\n\nLet us consider a set C of ‘n’ number of customers, the set R of ‘N’ number of reviews and \na set of significant features ′F ′\n\nx are considered. The corresponding vectors are represented \nas KC , KR and KFx . Then KRi is represented using a row vector and KFj is represented using \nthe column vector. Each entry KCm denote the number of times the  mth review arrives in \n\n\n\nPage 8 of 15Narayanan et al. J Big Data            (2020) 7:13 \n\ncustomers. The similarities between ith review of mth customer is found out using  L1 norm \nof KRi and KCm . The Distributed Memory-based resilient filter score δ is calculated using the \nEq. (5).\n\nThe δ score is calculated for each customer review whereas the score lies between [0,1]. \nThe significant features are found out using Eq. 4. For customer reviews without significant \nfeatures, �G value will be zero. The reviews with δ score value 0 are found to be insignificant \nwithout any significant feature or opinion and hence those reviews are eliminated and not \nconsidered for further processing in the work. More than one Distributed Memory-based \nresilient filter score value is identified then the second occurrence of the review is consid-\nered as duplicate.\n\nPrediction classifiers\n\nLogistic regression and Support Vector Machine classifiers are the supervised machine \nlearning approaches used in the proposed work for product pre-launch prediction.\n\nLogistic regression (LR)\n\nWe have implemented proposed model using logistic regression analysis for prediction. \nThis model predicts the failure or success of a new product in the market by analysing \nselected product features from customer reviews. A case study has been conducted using \nthe dataset of customer reviews of mobile phones. Success or failure is the predictor vari-\nable used for training and testing the dataset. For training the model 75% of the dataset is \nused and for testing the model, remaining 25% is used.\n\n• Let p be the prediction variable value, assigning 0 for failure and 1 for success.\n• p0 is the constant value.\n• b is the logarithmic base value.\n\nThen the logit function is,\n\nThen the Logistic regression value γ is shown in Eq. (7),\n\n(5)δ =\n\nN\nn\n�\n\ni = 1\n\nm = 1\n\n\n\n\n\n�\n\nKRi ∗\n\n�\n\n�x\nj=1 KFj\n\n��\n\n∗ KCm\n\nKRi · KCm\n\n\n\n ∗ |�G|\n\n(6)\nL0 = b\n\np0+p\nx\n∑\n\ni=1\n\nfi\n\n(7.1)γ =\nL0\n\n(\n\nbp0+p\n∑x\n\ni=1 fi\n)\n\n+ 1\n\n(7.2)=\n1\n\n1+ b\n−\n\n(\n\nb\np0+p\n\n∑x\ni=1\n\nfi\n)\n\n\n\nPage 9 of 15Narayanan et al. J Big Data            (2020) 7:13  \n\nThe probability value of γ lies between [0,1]. In this work, if this value is greater than 0.5 \nthe pre-launch prediction of the product is considered as success and for values less than \n0.5, it is considered as failure.\n\nSupport Vector Machine (SVM)\n\nSVM is the supervised machine learning method, used to learn from set of data to get new \nskills and knowledge. This classification method can learn from data features relationships \n( zi ) and its class \n\n(\n\nyi\n)\n\n that can be applied to predict the success or failure class the product \nbelongs to.\n\n• For a set T  of t training feature vectors, zi ∈ RD, where i = 1 to t.\n• Let yi ∈ {+1,−1} , where +1 belongs to product success class and -1 belongs to product \n\nfailure class.\n• The data separation occurs in the real numbers denoted as X in the D dimensional \n\ninput space.\n• Let w be the hyper plane normal vector element, where w ∈ XD.\n\nThe hyper plane is placed in such a way that distance between the nearest vectors of the \ntwo classes to the hyperplane should be maximum. Thus, the decision hyper plane is calcu-\nlated as,\n\nThe conditions for training dataset d ∈ X , is calculated as\n\nTo maximize the margin the value of w should be minimized.\nThe products in the positive one class (+1) are considered as successful products, [from \n\nEq. (9)] and those in the negative one class (−1) [from Eq. (10)] are in failure class.\n\nExperimental setup\n\nThe proposed system was implemented using Apache Spark 2.2.1 framework. Spark pro-\ngramming for python using PySpark version 2.1.2, which is the Spark python API has been \nused for the application development. An Ubuntu running Apache web server using Web \nServer Gateway Interface is used. Amazon Web Services is used to run some components \nof the software system large servers (nodes), having two Intel Xeon E5-2699V4 2.2 G Hz \nprocessors (VCPUs) with 4 cores and 16 GB of RAM on different Spark cluster configura-\ntions. According to the scalability requirements the software components can be config-\nured and can run on separate servers.\n\n(8)α(w) =\n2\n\n�w�\n\n(9)wtzi + d ≥ 1, where yi = +1.\n\n(10)wtzi + d ≤ −1, whereyi = yi − 1.\n\n\n\nPage 10 of 15Narayanan et al. J Big Data            (2020) 7:13 \n\nResults and discussions\nTo evaluate our prediction system several case studies have been conducted. Support \nVector Machine and Logistic regression classifiers are employed to perform the predic-\ntion. Most significant customer review features are used to analyse the system perfor-\nmance. The prediction accuracy evaluation is taken as one of the system design factors. \nThe system response time is another major concern for big data processing system. In \nthe customer review feature identification, we propose feature information gain and \nDMRDF approach to identify significant features and to eliminate redundant customer \nreviews from the input dataset.\n\nFigure  2 illustrates significant features required for the mobile phone sustainability. \nCustomer reviews and ratings of 7 brands of mobile phones are identified and evalu-\nated with DMRDF using SVM and LR. The graph shows the significant features identi-\nfied by the model against the percentage of customers whose reviews are analysed. 88% \nof the customers identified internal storage as a significant feature. Product price has \nbeen identified by 79% of customers as significant feature. With this evaluation customer \nrequirements for a product can be analysed in a better manner, thus can optimize the \ndesign of the product for better product quality and for product sustainability in the \nindustry.\n\nFigure 3 shows the comparison of the processing time taken by the proposed model \nwith different dataset size against that of the state of art techniques. DMRDF method \ntakes less time for completion of the application compared to other gini-index and latent \nsemantic analysis methods. Hence the proposed model is fast and scalable. It provides a \nhigh-speed processing performance with large datasets. This shows the DMRDF applica-\nbility in big data analytics, whereas gini-index and LSA-based methods processing time \nis larger for large volume of dataset. From the Fig. 3 it can be seen that with 9 GB dataset \ntime taken for prediction using LSA-based model, Gini-index model and DMRDF model \nis 342 s, 495 s and 156 s respectively. With 18 GB dataset time taken for prediction using \nLSA-based model, Gini-index model and DMRDF model 740 s, 910 s and 256 s respec-\ntively. Gini-index and LSA-based methods time taken for 18 GB dataset is twice that of \n9 GB dataset. But for DMRDF model time taken for 18 GB dataset is 1.6 times that of \n\n79%\n\n15%\n\n45%\n35%\n\n22%\n\n40%\n\n22%\n\n39%\n\n88%\n\n53%\n\n21%\n\n61%\n\n0%\n10%\n20%\n30%\n40%\n50%\n60%\n70%\n80%\n90%\n\n100%\n\nPe\nrc\n\nen\nta\n\nge\n o\n\nf C\nus\n\nto\nm\n\ner\ns\n\nIden�fied Significant Features\nFig. 2 Identified Significant Features from Customer reviews and Ratings\n\n\n\nPage 11 of 15Narayanan et al. J Big Data            (2020) 7:13  \n\n9 GB dataset and also it is 3 times lesser than Gini-index method. DMRDF model has \nmore advantage compared to the other state of art techniques in the case of application \nexecution and performance.\n\nThe reliability of the methods considered for the pre-launch prediction depends on \nprecision [44], recall and prediction accuracy measurement. Table 5 shows a comparison \nof precision, recall and accuracy measures of DMRDF, Gini-index and LSA-based meth-\nods with Support Vector Machine and Logistic Regression classifiers using customer \nreviews dataset over a period of 24 months. The results shown in Table 3 are best proved \nusing DMRDF with Support Vector Machine classification with prediction accuracy of \n95.4%. The DMRDF outperforms LSA-based and Gini-index methods in P@R, R@R and \nPA measures. Using proposed method, true positive (TP), false positive (FP), true nega-\ntive (TN) and false negative (FN) are found out. The prediction accuracy (PA), precision \n(P@R) and recall (R@R) are computed using Eqs. (10), (11), and (12) respectively.\n\n(10)PA =\nTP + TN\n\nTP + TN + FP + FN\n\n0\n\n100\n\n200\n\n300\n\n400\n\n500\n\n600\n\n700\n\n800\n\n900\n\n1000\n\n1GB 5GB 9GB 13GB 18GB\n\nGini-index\n\nDMRDF\n\nLSA-based\n\nTi\nm\n\ne \nTa\n\nke\nn \n\nin\n se\n\nc\n\nDataset size\nFig. 3 Dataset Size versus Processing Time Graph\n\nTable 3 Performance comparison of the proposed model with state of art techniques\n\nClassifier Support vector machine\n\nMethod used P@R (precision) PA % \n(prediction \naccuracy)\n\nDMRDF 0.941 0.92 95.4\n\nLSA-based 0.894 0.79 87.5\n\nGini-index 0.66 0.567 83.2\n\nClassifier Logistic regression\n\nMethod used P@R R@R % PA %\n\nDMRDF 0.915 0.849 93.5\n\nLSA-based 0.839 0.753 83\n\nGini-index 0.62 0.52 79.8\n\n\n\nPage 12 of 15Narayanan et al. J Big Data            (2020) 7:13 \n\nUsing DMRDF with SVM classifier and LR classifier, the prediction accuracy varia-\ntions are less compared to LSA-based and Gini-index methods. Hence DMRDF out-\nperforms the other two methods for customer review feature prediction.\n\nFurthermore Fig.  4, shows the DMRDF, LSA-based and Gini-index approaches as \napplied to the customer reviews and ratings datasets for 3, 6, 12, 18 and 24 months. \nIn DMRDF many features may appear in different customer review aspects, hence \nperformance evaluation will not consider duplicate customer reviews. In Gini- index, \nfeatures are extracted based on the polarity of the reviews and for large dataset P@R \nand R@R are less. The results show that DMRDF method outperforms the other two \nmethods in big data analysis. Gini-index approach does not perform well in customer \nreview feature prediction.\n\nConclusion and future work\nTechnological development in this era brings new challenges in artificial intelligence \nlike prediction, which is the next frontier for innovation and productivity. This work \nproposes the implementation of a scalable and reliable big data processing model \n\n(11)P@R =\nTP\n\nTP + FP\n\n(12)R@R =\nTP\n\nTP + FN\n\na SVM b SVM \n\n0.5\n\n0.6\n\n0.7\n\n0.8\n\n0.9\n\n1\n\n1.1\n\n3 6 12 18 24\n\nP@\nR\n\nReview in Months\n\nLSA-based DMRDF Gini-index\n\n0.5\n\n0.6\n\n0.7\n\n0.8\n\n0.9\n\n1\n\n1.1\n\n3 6 12 18 24\n\nR@\nR\n\nReview in Months\n\nLSA-based DMRDF Gini-index\n\nc Logistic Regression d Logistic Regression\n\n0.5\n\n0.6\n\n0.7\n\n0.8\n\n0.9\n\n1\n\n1.1\n\n3 6 12 18 24\n\nP@\nR\n\nReview in Months\n\nLSA-based DMRDF Gini-index\n\n0.5\n\n0.6\n\n0.7\n\n0.8\n\n0.9\n\n1\n\n1.1\n\n3 6 12 18 24\n\nR@\nR\n\nReview in Months\n\nLSA-based DMRDF Gini-index\n\nFig. 4 Precision and Recall of DMRDF, LSA-based and Gini-index methods using SVM and LR classifiers\n\n\n\nPage 13 of 15Narayanan et al. J Big Data            (2020) 7:13  \n\nwhich identify significant features and eliminates redundant data using Feature Infor-\nmation Gain and Distributed Memory-based Resilient Dataset Filter method with \nLogistic Regression and Support Vector Machine prediction classifiers. A compari-\nson of the analysis has been conducted with state of art techniques like Gini-index \nand LSA-based approaches. The prediction accuracy, precision and recall of DMRDF \nmethod outperforms the other methods. Results show that the prediction accuracy \nof the proposed method increases by 10% using significant feature identification and \nelimination of redundancy from dataset compared to state of art techniques. Large \nfeature dimensionality reduces the prediction accuracy of the LSA-based method \nwhere as number of significant features plays an important role in prediction model-\nling. Results show that proposed DMRDF model is scalable and with huge volume of \ndataset model performance is good as well as time taken for processing the applica-\ntion is less compared to state of art techniques.\n\nResilience property of DMRDF method have long lineage, hence this can achieve \nfault-tolerance. DMRDF model is fast because of the in-memory computation \nmethod. Proposed design can be extended to other product feature identification big \ndata processing domains. As a future work, the model may be developed to make real \ntime streaming predictions through a unified API that searches customer comments, \nratings and surveys from different reliable online websites concurrently to obtain syn-\nthesis of sentiments with an information fusion approach. Since the statistical prop-\nerties of customer reviews and ratings vary over time, the performance of machine \nlearning algorithms can also come down. To cope wit",
      "metadata_storage_path": "aHR0cHM6Ly9jb3Jwb3JhdGV0cmFpbmRhdGEuYmxvYi5jb3JlLndpbmRvd3MubmV0L3BhcGVycy9zNDA1MzctMDIwLTAwMjkyLXkucGRm0",
      "keyphrases": [
        "Distributed Memory-based Resilient Dataset Filter",
        "Improving prediction"
      ],
      "title": "Improving prediction with enhanced Distributed Memory-based Resilient Dataset Filter",
      "author": "Sandhya Narayanan ",
      "publicationName": "Journal of Big Data",
      "publisher": "Springer",
      "doi": "10.1186/s40537-020-00292-y",
      "publicationDate": "2020-02-28"
    },
    {
      "@search.score": 0.8288425,
      "content": "\nQER: a new feature selection method \nfor sentiment analysis\nTuba Parlar1* , Selma Ayşe Özel2 and Fei Song3\n\nIntroduction\n“What other people think” has always been an important piece of information for most \nof us during the decision making process [1]. The Internet and social media provide a \nmajor source of information about people’s opinions. Due to the rapidly-growing num-\nber of online documents, it becomes both time-consuming and hard to obtain and ana-\nlyze the desired opinionated information. Turkey is among the top 20 countries with the \nhighest numbers of Internet users according to the Internet World Stats.1 The exploding \ngrowth in the Internet users is one of the main reasons that sentiment analysis for differ-\nent languages and domains becomes an actively-studied area for many researchers \n[2–6].\n\nSentiment analysis (SA) is a natural language processing task that classifies the senti-\nments expressed in review documents as “positive” or “negative”. In general, SA is con-\nsidered as a two-class classification problem. However, some researchers use “neutral” as \n\n1 http://www.internetworldstats.com/.\n\nAbstract \n\nSentiment analysis is about the classification of sentiments expressed in review docu-\nments. In order to improve the classification accuracy, feature selection methods are \noften used to rank features so that non-informative and noisy features with low ranks \ncan be removed. In this study, we propose a new feature selection method, called \nquery expansion ranking, which is based on query expansion term weighting meth-\nods from the field of information retrieval. We compare our proposed method with \nother widely used feature selection methods, including Chi square, information gain, \ndocument frequency difference, and optimal orthogonal centroid, using four classi-\nfiers: naïve Bayes multinomial, support vector machines, maximum entropy model-\nling, and decision trees. We test them on movie and multiple kinds of product reviews \nfor both Turkish and English languages so that we can show their performances for \ndifferent domains, languages, and classifiers. We observe that our proposed method \nachieves consistently better performance than other feature selection methods, and \nquery expansion ranking, Chi square, information gain, document frequency difference \nmethods tend to produce better results for both the English and Turkish reviews when \ntested using naïve Bayes multinomial classifier.\n\nKeywords: Sentiment analysis, Feature selection, Machine learning, Text classification\n\nOpen Access\n\n© The Author(s) 2018. This article is distributed under the terms of the Creative Commons Attribution 4.0 International License \n(http://creativecommons.org/licenses/by/4.0/), which permits unrestricted use, distribution, and reproduction in any medium, \nprovided you give appropriate credit to the original author(s) and the source, provide a link to the Creative Commons license, and \nindicate if changes were made.\n\nRESEARCH\n\nParlar et al. Hum. Cent. Comput. Inf. Sci.  (2018) 8:10 \nhttps://doi.org/10.1186/s13673-018-0135-8\n\n*Correspondence:   \ntparlar@mku.edu.tr \n1 Department \nof Mathematics, Mustafa \nKemal University, Antakya, \nHatay, Turkey\nFull list of author information \nis available at the end of the \narticle\n\nhttp://orcid.org/0000-0002-8004-6150\nhttp://www.internetworldstats.com/\nhttp://creativecommons.org/licenses/by/4.0/\nhttp://crossmark.crossref.org/dialog/?doi=10.1186/s13673-018-0135-8&domain=pdf\n\n\nPage 2 of 19Parlar et al. Hum. Cent. Comput. Inf. Sci.  (2018) 8:10 \n\nthe third class label. There are a number of studies about sentiment analysis that use dif-\nferent approaches for data preprocessing, feature selection, and sentiment classification \n[1, 3, 4, 6–10]. The statistical methods such as Chi square (CHI2) and information gain \n(IG) are used to eliminate unnecessary or irrelevant features so that the classification \nperformance can be improved [11]. Supervised learning methods including naïve Bayes \n(NB), support vector machines (SVM), decision trees (DT), and maximum entropy mod-\nelling (MEM) are used to classify the sentiments of the reviews.\n\nAlthough SA can be considered as a text classification task, it has some differences \nfrom the traditional topic-based text classification. For example, instead of saying: “This \ncamera is great. It takes great pictures. The LCD screen is great. I love this camera” in a \nreview document, people are more likely to write: “This camera is great. It takes breath-\ntaking pictures. The LCD screen is bright and clear. I love this camera.” [8]. As can be \nseen, sentiment-expressing words like “great” are not so frequent within a particular \nreview, but can be more frequent across different reviews, and a good feature selection \nmethod for SA should take this observation into account.\n\nIn this paper, we propose a new feature selection method, called query expansion rank-\ning (QER) which is especially developed for reducing dimensionality of feature space of \nSA problems. The aim of this study is to show that our proposed method is effective for \nSA from review texts written in different languages (e.g., Turkish, English) and domains \n(e.g., movie reviews, book reviews, kitchen appliances reviews, etc.). QER is based on \nquery expansion term weighting methods used to improve the search performance of \ninformation retrieval systems [12, 13] and to evaluate its effectiveness as a feature selec-\ntor in SA, we compare it with other common feature selection methods, including CHI2, \nIG, document frequency difference (DFD), and optimal orthogonal centroid (OCFS), \nalong with four text classifiers: naïve Bayes multinomial (NBM), SVM, DT, and MEM, \nover ten different review documents datasets. Our goal is to examine whether these fea-\nture selection methods can reduce the feature sizes and improve the classification accu-\nracy of sentiment analysis with respect to different document domains, languages, and \nclassifiers.\n\nThe rest of the paper is organized as follows. “Related work” reviews the related work \non sentiment analysis. “Methods” presents the methods that we used for our study, \nincluding the new feature selection method we proposed. “Experiments and results” \ndescribes the experimental settings, datasets, performance measures, and testing results. \nFinally, “Conclusion” concludes the paper.\n\nRelated work\nSA is an important topic in Natural Language Processing and Artificial Intelligence. \nAlso known as opinion mining, SA mines people’s opinions, sentiments, evalua-\ntions, and emotions about entities such as products, services, organizations, individu-\nals, issues, and events, as well as their related attributes. This kind of analysis has many \nuseful applications. For example, it determines a product’s popularity according to \nthe user’s reviews. If the overall sentiments are negative, further analysis may be per-\nformed to identify which features contribute to the negative ratings so companies can \nreshape their businesses. Numerous studies have been done for sentiment analysis in \ndifferent domains, languages, and approaches [3–5, 8–10, 14–17]. Among these studies, \n\n\n\nPage 3 of 19Parlar et al. Hum. Cent. Comput. Inf. Sci.  (2018) 8:10 \n\nthe machine learning approaches are more popular since the models can be automati-\ncally trained and improved with the training datasets. Pang et al. [4] apply supervised \nmachine learning methods such as NB and SVM to sentiment classification. NB, SVM, \nMEM, and DT are some of the commonly used machine learning approaches [4, 7–9, \n14]. Feature selection methods are used to rank features so that non-informative features \ncan be removed to improve the classification performance [18]. Some researchers have \ninvestigated the effects of feature selection for sentiment analysis [3, 8–10, 19–25]. For \nexample, Yang and Yu [3] examine IG for feature selection and evaluate its performance \nusing NB, SVM, and C4.5 (popular implementation for DT) classifiers. Nicholls et al. [8] \ncompare their proposed DFD feature selection method against other feature selection \nmethods, including CHI2, OCFS [26], and count difference using the MEM classifier. \nAgarwal et al. [9] investigate minimum redundancy maximum relevancy (mRMR) and \nIG methods for sentiment classification using NBM and SVM classifiers. The results \nshow that mRMR performs better than IG for feature selection, and NBM performs bet-\nter than SVM in accuracy and execution time. Abbasi et al. [22] examine a new feature \nselection method called entropy weighted genetic algorithm (EWGA) and compare the \nperformance of this method using information gain feature selection method. EWGA \nachieves a relatively high accuracy of 91.7% using SVM classifier. Xia et al. [24] design \ntwo types of feature sets: POS based and word relation based. Their word relation based \nmethod improves an accuracy of 87.7 and 85.15% on movie and product datasets. Bai \n[25] proposes a Tabu heuristic search-enhanced Markov blanket model that provides a \nvocabulary to extract sentiment features. Their method achieves an accuracy of 92.7% \nfor the movie review dataset. Mladenovic et al. [16] propose a feature selection method \nthat is based on mapping of a large number of related features to a few features. Their \nproposed method improves the classification performance using unigram features \nwith 95% average accuracy. Zheng et al. [27] perform comparative experiments to test \ntheir proposed improved document frequency feature selection method. Their method \nachieves significant improvement in sentiment analysis of Chinese online reviews with \nan accuracy of 97.3%.\n\nMost of the SA studies listed above focus on the English language. Only few studies \nhave been done on SA for the Turkish language [6, 10, 19, 28–31]. The Turkish language \nbelongs to the Altaic branch of the Ural-Altaic family of languages and is mainly used in \nthe Republic of Turkey. Turkish is an agglutinative language similar to Finnish and Hun-\ngarian, where a single word can be translated into a relatively longer sentence in English \n[32]. For instance, word “karşılaştırmalısın” in Turkish can be expressed as “you must \nmake (something) compare” in English. As Turkish and English have different charac-\nteristics, methods developed for SA in English need to be tested for Turkish. Among \nthe few researchers who investigate the effects of feature selection on the SA of Turkish \nreviews, Boynukalın [29] applies Weighted Log Likelihood Ratio (WLLR) to reduce fea-\nture space with NB, Complementary NB, and SVM classifiers for the emotional analysis \nusing the combinations of n-grams where sequences of n words are considered together. \nIt is shown that WLLR helps to improve the accuracy with reduced feature sizes. Akba \net al. [19] implement and compare the performance of reduced feature sizes using two \nfeature selection methods: CHI2 and IG with NB and SVM classifiers. They show that \nfeature selection methods improve the classification accuracy.\n\n\n\nPage 4 of 19Parlar et al. Hum. Cent. Comput. Inf. Sci.  (2018) 8:10 \n\nOur aim is to propose a new feature selection method for the SA of Turkish and Eng-\nlish reviews. We presented an initial version of this method in [10] where we employ \nonly product review dataset in Turkish and compare our method with CHI2 and DFD \nby using only one classifier. We now extend it to more datasets for Turkish, and also \ninvestigate the performance of our method in English datasets to show that our method \nis language independent. We further include more feature selection methods especially \ndeveloped for SA and compare the performance of our proposed method using NBM, \nSVM, MEM, and DT classifiers along with statistical analysis to prove that our method is \nclassifier independent.\n\nMethods\nMachine learning algorithms\n\nFor sentiment classification, we use the Weka [33] data mining tool, which contains the \nfour classifiers we use in our experiments, i.e., NBM, SMO for SVM, J48 for C4.5, and LR \nfor MEM. We choose NBM, SVM, LR, and J48 classification methods due to the follow-\ning reasons: (i) many researchers use NBM for text classification because it is computa-\ntionally efficient [9, 10, 14] and performs well for large vocabulary sizes [34]; (ii) SVM \ntends to perform well for traditional text classification tasks [3, 4, 7, 14, 35]; (iii) LR is \nknown to be equivalent to MEM which is another method used in SA studies [8]; (iv) J48 \nis a well-known decision tree classifier for many classification problems and is used for \nSA [3, 30].\n\nFeature selection\n\nFeature Selection methods have been shown to be useful for text classification in general \nand sentiment analysis in specific [11, 18]. Such methods rank features according to cer-\ntain measures so that non-informative features can be removed, and at the same time, \nthe most valuable features can be kept in order to improve the classification accuracy \nand efficiency. In this study, we consider several feature selection methods, including \ninformation gain, Chi square, document frequency difference, optimal orthogonal cen-\ntroid, and our new query expansion ranking (QER) so that we can compare their effec-\ntiveness for the sentiment analysis.\n\nFeature sizes are selected in the range from 500 to 3000 with 500 increments, com-\npared with the total feature sizes ranging from 8000 to 18,000 for the Turkish review \ndatasets and from 8000 to 38,000 for English review datasets. In our previous study [10], \nwe observed that feature sizes up to 3000 tend to give good classification performance \nimprovement; therefore we choose these feature sizes in our experiments.\n\nInformation gain\n\nInformation gain is one of the most common feature selection methods for sentiment \nanalysis [3, 9, 19, 35], which measures the content of information obtained after knowing \nthe value of a feature in a document. The higher the information gain, the more power \nwe have to discriminate between different classes.\n\nThe content of information can be calculated by the entropy that captures the uncer-\ntainty of a probability distribution for the given classes. Given m number of classes: \nC = {c1,c2,…,cm} the entropy can be given as follows:\n\n\n\nPage 5 of 19Parlar et al. Hum. Cent. Comput. Inf. Sci.  (2018) 8:10 \n\nwhere P(ci) is the probability of how many documents in class ci. If an attribute A has n \ndistinct values: A = {a1,a2,…,an}, then the entropy after the attribute A is observed can be \ndefined as follows:\n\nwhere P(aj) is the probability of how many documents contain the attribute value aj, and \nP(ci|aj) is the probability of how many documents in class ci that contain the attribute \nvalue aj. Based on the definitions above, the information gain for an attribute is simply \nthe difference between the entropy values before and after the attribute is observed:\n\nFor sentiment analysis, we normally classify the reviews into positive and negative cat-\negories, and for each keyword, it either occurs or does not occur in a given document; so \nthe above formulas can be further simplified. Nevertheless, we can cut down the number \nof features in the same way by choosing the keywords that have high information gain \nscores.\n\nChi square (CHI2)\n\nChi square measures the dependence between a feature and a class. A higher score \nimplies that the related class is more dependent on the given feature. Thus, a feature with \na low score is less informative and should be removed [3, 8, 10, 19]. Using the 2-by-2 \ncontingency table for feature f and class c, where A is the number of documents in class c \nthat contains feature f, B is the number of documents in the other class that contains f, C \nis the number of documents in c that does not contain f, D is the number of documents \nin the other class that does not contain f, and N is the total number of documents, then \nthe Chi square score can be defined in the following:\n\nThe Chi square statistics can also be computed between a feature and a class in the \ndataset, which are then combined across all classes to get the scores for each feature as \nfollows:\n\nOne problem with the CHI2 method is that it may produce high scores for rare features \nas long as they are mostly used for one specific class. This is a bit counter-intuitive, since \nrare features are not frequently used in text and thus do not have a big impact for text \n\n(1)H(C) = −\n\nm\n∑\n\ni=1\n\nP(ci) log2 P(ci)\n\n(2)H(C|A) =\n\nn\n∑\n\nj=1\n\n(\n\n−P(aj)\n\nm\n∑\n\ni=1\n\nP(ci|aj) log2P(ci|aj)\n\n)\n\n(3)IG(A) = H(C)−H(C|A)\n\n(4)χ2\n(\n\nf , c\n)\n\n=\nN (AD − CB)2\n\n(A+ C)(B+ D)(A+ B)(C + D)\n\n(5)χ2(f ) =\n\nm\n∑\n\ni=1\n\nP(ci)χ\n2(f , ci)\n\n\n\nPage 6 of 19Parlar et al. Hum. Cent. Comput. Inf. Sci.  (2018) 8:10 \n\nclassification. For SA, however, this is not a big issue since many sentiment-expressing \nfeatures are not frequently used within an individual review.\n\nDocument frequency difference\n\nInspired by the observation that sentiment-expressing words tends to be less frequent \nwithin a review, but more frequent across different reviews, Nicholls and Song [8] pro-\npose the DFD method that tries to differentiate the features for positive and negative \nclasses, respectively, across a document collection. More specifically, DFD is calculated \nas follows:\n\nwhere DFf\n+ is the number of documents in the positive class that contain feature f, DFf\n\n− \nis the number of documents in the negative class that contain f, and N is the total num-\nber of documents in the dataset. Note that all scores are normalized between 0 and 1; \nso they should be proportional for us to rank the features in a document collection. For \nexample, a non-sentiment word may have similar document frequencies in both posi-\ntive and negative classes, and will get a low score, but a sentiment word for the positive \nclass may have a bigger difference, resulting in a higher score. One limitation of the DFD \nmethod is that it requires an equal or nearly equal number of documents in both classes, \nwhich is more or less true for the datasets used in our experiments.\n\nOptimal orthogonal centroid (OCFS)\n\nOCFS method is an optimized form of the orthogonal centroid algorithm [26]. Docu-\nments are represented as high dimensional vectors where the weights of each dimension \ncorrespond to the importance of the related features, and a centroid is simply the aver-\nage vector for a set of document vectors. OCFS aims at finding a subset of features that \ncan make the sum of distances between all the class means maximized in the selected \nsubspace. The score of a feature f by OCFS is defined in the following [8]:\n\nwhere Nc is the number of documents in class c, N is the number of documents in the \ndataset, mc is the centroid for class c, m is the centroid for the dataset D, and mf, mc\n\nf are \nthe values of feature f in centroid m, mc respectively. The centroids of m and mc are cal-\nculated as follows:\n\nQuery expansion ranking\n\nQuery expansion ranking method is our proposed feature selection method inspired \nby the query expansion methods from the field of information retrieval (IR). Query \n\n(6)Scoref =\n|DF\n\nf\n+ − DF\n\nf\n−|\n\nN\n\n(7)Scoref =\n∑\n\nc\n\nNc\n\nN\n\n(\n\nm\nf\nc −mf\n\n)2\n\n(8)mc =\n\n∑\n\nxi∈c\nxi\n\nNc\n\n(9)m =\n\n∑\n\nxi∈D\nxi\n\nN\n\n\n\nPage 7 of 19Parlar et al. Hum. Cent. Comput. Inf. Sci.  (2018) 8:10 \n\nexpansion helps to find more relevant documents for a given query. It does so by adding \nnew terms to the query. The new terms are selected from documents that are relevant \nto the original query so that the expanded query can retrieve more relevant documents. \nMore specifically, terms from the relevant documents are extracted along with some \nscores, and those with the highest scores are included in the expanded query.\n\nWe propose a new feature selection method inspired by the query expansion technique \ndeveloped for probabilistic weighting model proposed by Harman [12]. Harman [12, 36] \nstudies how to assign scores to terms extracted from relevant documents for a given \nquery Q so that high scored terms are used to expand the original query and improve \nprecision of information retrieval strategy. In this method, first, query Q is sent to the \ninformation retrieval system, and then the system returns documents that are found as \nrelevant to the user. Then, user examines the returned documents and marks the ones \nthat are relevant with the query. After that, all the terms in the relevant documents are \nextracted and they are assigned scores by using a score formula as proposed by Har-\nman [12], and top scored k terms are chosen as the most valuable terms to expand the \nquery. Then, the expanded query Q’, which includes the terms in the original query plus \nthe k new terms that have the top-k scores, is sent to the information retrieval system to \nreturn more relevant documents to the original query Q. Equation 10 presents the score \nformula developed by Harman [12] to calculate ranking score of a term f extracted from \nthe set of relevant documents for a given query Q.\n\nwhere pf is the probability of term f in the set of relevant documents for query Q, and qf \nis the probability of term f in the set of non-relevant documents for query Q. These prob-\nability scores are computed according to Robertson and Sparck Jones [13].\n\nWe revise the above score computation method to develop an efficient feature selector \nfor SA. In our feature selection method, we propose a score formula given in Eq. 11 to \ncompute scores for features:\n\nwhere pf is the ratio of positive documents containing feature f and qf is the ratio of \nnegative documents containing feature f, which are computed according to Eqs. 12, 13, \nrespectively:\n\n(10)Scoref = log2\npf\n(\n\n1− qf\n)\n\n(\n\n1− pf\n)\n\nqf\n\n(11)Scoref =\npf + qf\n∣\n\n∣pf − qf\n∣\n\n∣\n\n(12)pf =\nDF\n\nf\n+ + 0.5\n\nN+ + 1.0\n\n(13)qf =\nDF\n\nf\n− + 0.5\n\nN− + 0.5\n\n\n\nPage 8 of 19Parlar et al. Hum. Cent. Comput. Inf. Sci.  (2018) 8:10 \n\nwhere DFf\n+ and DFf\n\n− are the raw counts of documents that contain f in the positive and \nnegative classes, respectively and N+ and N− are the numbers of documents in the \npositive and negative classes, respectively. In the probability calculations, we add small \nconstants to the numerators and denominators in Eqs. 12, 13 following Robertson and \nSparck Jones [13] who add similar constants to avoid having zero probabilities. Such a \nmethod is known as data smoothing in statistical language processing.\n\nIn QER feature selection method, scores of features are computed before the features \nhaving the lowest scores are selected and used in the classification process. When a fea-\nture has low score, the difference between the probabilities for the positive and negative \nclasses is high; therefore the feature is more class specific and more valuable for clas-\nsification process. Among the feature selection methods we considered, we notice that \nIG and OCFS are good at distinguishing multiple classes, while CHI2, DFD, and QER \nare restricted to two classes, although all of them are suitable for sentiment analysis. IG \nis considered as a greedy approach since it favors those that can maximize the informa-\ntion gain for separating the related classes. Although CHI2 tries to identify the features \nthat are dependent to a class, it can also give high values to rare features that only affect \nfew documents in a given collection. OCFS has been shown to be effective for tradi-\ntional topic-based text classification, but it depends on the distance/similarity measures \nbetween the vectors of the related documents. Since sentiment-expressing features do \nnot happen frequently within a review, as illustrated by the example in the introduction, \nthey may not be favored by the OCFS method. QER is similar to DFD in that they both \nrely on the differences of the document frequencies of a given feature between the two \nclasses. However, QER is different from DFD in that it normalizes the document fre-\nquencies of a feature in both classes into probabilities and uses the ratio of the sum over \nthe difference for these two probabilities.\n\nExperiments and results\nDatasets\n\nWe use Turkish and English review datasets in our experiments. The Turkish movie \nreviews are collected from a publicly available website (http://www.beyazperde.com) \n[30]. The dataset has 1057 positive and 978 negative reviews. The Turkish product review \ndataset is collected from an e-commerce website (http://www.hepsiburada.com) from \ndifferent domains [28]. It consists of four subsets of reviews about books, DVDs, elec-\ntronics, and kitchen appliances, each of which has 700 positive and 700 negative reviews. \nTo compare our results with existing work for sentiment analysis, we use similar datasets \nfor English reviews. The English movie review dataset is introduced by Pang and Lee [7], \nand consists of 1000 positive and 1000 negative reviews. English product review dataset \nis introduced by Blitzer et al. [37] and also has four subsets: books, DVDs, electronics, \nand kitchen appliances, with 1000 positive and 1000 negative reviews for each subset. In \norder to keep the same dataset sizes with Turkish product reviews, we randomly select \n700 positive and 700 negative reviews from each subset of the English product reviews.\n\nPerformance evaluation\n\nThe performance of a classification system is typically evaluated by F measure, which \nis a composite score of precision and recall. Precision (P) is the number of correctly \n\nhttp://www.beyazperde.com\nhttp://www.hepsiburada.com\n\n\nPage 9 of 19Parlar et al. Hum. Cent. Comput. Inf. Sci.  (2018) 8:10 \n\nclassified items over the total number of classified items with respect to a class. Recall \n(R) is the number of correctly classified items over the total number of items that belong \nto a given class. Together, the F measure gives the harmonic mean of precision and \nrecall, and is calculated as follows [33]:\n\nSince we are doing multi-fold cross validations in our experiments, we use the micro-\naverage of F measure for the final classification results. This is done by adding the clas-\nsification results for all documents across all five folds before computing the final P, R, \nand the F.\n\nExperimental settings\n\nWe conduct the experiments on a MacBook Pro with 2.5 GHz Intel Core i7 processor \nand 16 GB 1600 MHz DDR3. We use Python with NLTK [38] library in our experiments. \nAfter tokenizing text into words along with case normalization, we keep some punctua-\ntion marks and stop words, as they may express sentiments (e.g., punctuation marks like \nexclamation and question marks, and stop words like “too” in “too expensive”). In addi-\ntion, we do not apply stemming as Turkish is an agglutinative language and the polarity \nof a word is often included in the suffixes. Therefore, we can have a large feature space \nand it becomes important to apply feature selection methods to reduce this space. For \nsentiment classification, we use the Weka [33] data mining tool, which contains the four \nclassifiers we use in our experiments, i.e., NBM, SMO for SVM, J48 for C4.5, and LR for \nMEM. Since our datasets are relatively small with at most a couple of thousands of docu-\nments, we apply the fivefold cross validation, which divides a dataset into five portions: \nfour of them are used for training and the remaining one for testing, and then these por-\ntions are rotated to get a total of five F measures. Table 1 the average F measures for all \nthe classifiers where the whole feature spaces are used for each dataset, except the LR \nclassifier since it requires too much memory to handle the whole feature spaces for these \ndatasets. As can be seen in Table  1, the total number of features without any reduc-\ntion ranges from 9000 to 18,000 for the Turkish review datasets, and 8,000–38,000 for \nthe English review datasets. These results form the baselines of our study and any new \nresults obtained with feature selection methods by applying five folds cross validation \ncan be compared for possible improvements.\n\n(14)F = 2×\nP × R\n\nP + R\n\nTable 1 Baseline results in F measure for the Turkish and English review datasets\n\nTurkish review datasets English review datasets\n\nFeatures NBM SVM J48 LR Features NBM SVM J48 LR\n\nMovie 18,578 0.8248 0.8161 0.6954 – 38,869 0.8129 0.8480 0.6769 –\n\nDVDs 11,343 0.7957 0.7320 0.6886 – 17,674 0.7836 0.7649 0.6789 –\n\nElectronics 10,911 0.8155 0.7707 0.7371 – 9010 0.7629 0.7856 0.6750 –\n\nBook 10,511 0.8317 0.7955 0.7019 – 18,306 0.7619 0.7485 0.6407 –\n\nKitchen 9447 0.7762 0.7407 0.6647 – 8076 0.8099 0.8136 0.7093 –\n\n\n\nPage 10 of 19Parlar et al. Hum. Cent. Comput. Inf. Sci.  (2018) 8:10 \n\nPerformance of feature selection methods for Turkish reviews\n\nWe tested five feature selection methods: QER, CHI2, IG, DFD, and OCFS on both \nTurkish and English review datasets. For each feature selection method, we tried six fea-\nture sizes at 500, 1000, 1500, 2000, 2500, and 3000, since this is the range typically con-\nsidered for text classification, and in terms of total features, we have 9000–18,000 for the \nTurkish review datasets, and 8000–38,000 for English review datasets from our baseline \nsystems. In our previous study [10], we also observed that feature sizes up to 3000 tend \nto give good classification performance. For all feature selection methods, we pick the \ntop-ranked features of a desirable size n based on the scores of the related formulas for \nthese methods. All of these settings are run against four classifiers: NBM, SVM, LR, and \nJ48, resulting in a total of 120 experiments for each review dataset. Table 2 summarizes \nthe best results for all pairs of feature selection methods and Turkish review datasets. \nFor each pair, we show the best micro-average F measure along with the correspond-\ning classifier and feature size. Also, the best results for each review dataset are given in \nbold-face.\n\nAs observed in Table 2, our new method QER is the best performer for each review \ndataset. CHI2 and IG have almost the same performance for the Turkish reviews and \nhave better results than DFD and OCFS for the movie, book, DVDs, and kitchen review \ndatasets. DFD with NBM classifier has better results than CHI2, IG, and OCFS for the \nelectronics review dataset. Also, CHI2, IG, and QER tend to work well with smaller fea-\nture sizes, while DFD and OCFS tend to favour bigger feature sizes. Note that DFD does \nreasonably well across all review datasets, which confirms our intuition that sentiment-\nexpressing words usually have low frequencies within a document, but relatively high \nfrequencies across different documents. Although OCFS is quite robust for traditional \ntopical text classification as reported in Cai and Song [39], it is not doing well for senti-\nment analysis, perhaps for the same intuition as we just explained for DFD. Once again, \nNBM remains to be the best for most of our experiments except that SVM does the best \nfor the kitchen reviews when analysed with the CHI2 and IG methods. When analysed \nby univariate ANOVA and post hoc tests for the book, DVDs, electronics, and kitchen \nreview datasets, we found that there are significant differences between three groups \n(Baseline and OCFS), (DFD, CHI2, and IG) and (QER) at 95% confidence level. Within \neach group, however, there are no significant differences. For the movie review dataset, \nthere are significant differences between two groups (Baseline and OCFS), and (DFD, \nCHI2, IG, and QER) at the 95% confidence level. Overall, feature selection methods are \nshown to be effective for sentiment analysis, improving significantly over the baseline \nresults.\n\nTo examine the effects of text classifiers, we show the best classification results for \npairs of feature selection methods and text classifiers on the electronic review dataset in \nTable 3. Note that NBM does the best for all review datasets; J48 the worst; and SVM and \nLR in between, although LR is consistently better than SVM except for the QER method. \nOne reason that the decision-tree-based solution J48 does not do well for text classifi-\ncation in general [40] and sentiment analysis in specific is that it is a greedy approach, \nalways trying to find the features that separate the given classes the most. As a result, the \nclassifier may use a much smaller set of features, even though there are many more rel-\nevant features are available. SVM typically does well for the traditional topic-based text \n\n\n\nPage 11 of 19Parlar et al. Hum. Cent. Comput. Inf. Sci.  (2018) 8:10 \n\nTa\nb\n\nle\n 2\n\n T\nh\n\ne \nb\n\nes\nt c\n\nla\nss\n\nifi\nca\n\nti\no\n\nn\n r\n\nes\nu\n\nlt\ns \n\nfo\nr \n\np\nai\n\nrs\n o\n\nf f\nea\n\ntu\nre\n\n s\nel\n\nec\nti\n\no\nn\n\n m\net\n\nh\no\n\nd\ns \n\nan\nd\n\n th\ne \n\nTu\nrk\n\nis\nh\n\n r\nev\n\nie\nw\n\n d\nat\n\nas\net\n\ns\n\nQ\nER\n\nD\nFD\n\nO\nC\n\nFS\nC\n\nH\nI2\n\nIG\n\nSi\nze\n\nF \nm\n\nea\nsu\n\nre\nSi\n\nze\nF \n\nm\nea\n\nsu\nre\n\nSi\nze\n\nF \nm\n\nea\nsu\n\nre\nSi\n\nze\nF \n\nm\nea\n\nsu\nre\n\nSi\nze\n\nF \nm\n\nea\nsu\n\nre\n\nM\no",
      "metadata_storage_path": "aHR0cHM6Ly9jb3Jwb3JhdGV0cmFpbmRhdGEuYmxvYi5jb3JlLndpbmRvd3MubmV0L3BhcGVycy9zMTM2NzMtMDE4LTAxMzUtOC5wZGY1",
      "keyphrases": [
        "new feature selection method",
        "sentiment analysis",
        "QER"
      ],
      "title": "QER: a new feature selection method for sentiment analysis",
      "author": "Tuba Parlar ",
      "publicationName": "Human-centric Computing and Information Sciences",
      "publisher": "Springer",
      "doi": "10.1186/s13673-018-0135-8",
      "publicationDate": "2018-05-09"
    }
  ]
}
```