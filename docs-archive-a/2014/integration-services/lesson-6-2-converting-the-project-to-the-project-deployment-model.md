---
title: '2단계: 프로젝트를 프로젝트 배포 모델로 변환 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 80964293-f1f5-4da7-b1fb-00ab8c30c1c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a7b879b2bea4afd58a48cdfc6f0890353fe6758
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647104"
---
# <a name="step-2-converting-the-project-to-the-project-deployment-model"></a><span data-ttu-id="1f95f-102">2단계: 프로젝트를 프로젝트 배포 모델로 변환</span><span class="sxs-lookup"><span data-stu-id="1f95f-102">Step 2: Converting the Project to the Project Deployment Model</span></span>
  <span data-ttu-id="1f95f-103">이 작업에서는 프로젝트를 프로젝트 배포 모델로 변환하기 위해 Integration Services 프로젝트 변환 마법사를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1f95f-103">In this task, you will use the Integration Services Project Conversion Wizard to convert the project to the Project Deployment Model.</span></span>  
  
### <a name="converting-the-project-to-the-project-deployment-model"></a><span data-ttu-id="1f95f-104">프로젝트를 프로젝트 배포 모델로 변환</span><span class="sxs-lookup"><span data-stu-id="1f95f-104">Converting the Project to the Project Deployment Model</span></span>  
  
1.  <span data-ttu-id="1f95f-105">프로젝트 메뉴에서 프로젝트 배포 모델로 변환을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f95f-105">On the Project Menu, click Convert to Project Deployment Model.</span></span>  
  
2.  <span data-ttu-id="1f95f-106">Integration Services 프로젝트 변환 마법사 소개 페이지에서 단계를 검토한 후 다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f95f-106">On the Integration Services Project Conversion Wizard Introduction page, review the steps then click Next.</span></span>  
  
3.  <span data-ttu-id="1f95f-107">패키지 선택 페이지의 패키지 목록에서 Lesson 6.dtsx를 제외한 모든 확인란의 선택을 취소한 후 다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f95f-107">On the Select Packages page, in the Packages list, clear all checkboxes except Lesson 6.dtsx then click Next.</span></span>  
  
4.  <span data-ttu-id="1f95f-108">프로젝트 속성 지정 페이지에서 다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f95f-108">On the Specify Project Properties page, click Next.</span></span>  
  
5.  <span data-ttu-id="1f95f-109">실행 패키지 태스크 업데이트 페이지에서 다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f95f-109">On the Update Execute Package Task page click Next.</span></span>  
  
6.  <span data-ttu-id="1f95f-110">구성 선택 페이지의 구성 목록에서 Lesson 6.dtsx 패키지가 선택되었는지 확인한 후 다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f95f-110">On the Select Configurations page, make sure the Lesson 6.dtsx package is selected in the Configurations list, then click Next.</span></span>  
  
7.  <span data-ttu-id="1f95f-111">매개 변수 만들기 페이지에서 Lesson 6.dtsx 패키지가 선택되었는지 확인하고 구성 속성 목록에서 범위를 패키지로 설정한 후 다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f95f-111">On the Create Parameters page make sure the Lesson 6.dtsx package is selected, and the Scope is set to Package, in the Configuration Properties List, then Click Next.</span></span>  
  
8.  <span data-ttu-id="1f95f-112">구성 속성 페이지에서 이름 및 값이 변수 및 구성 값에 대한 Lesson 5에서 지정된 이름 및 값과 동일한지 확인한 후 다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f95f-112">On the Configure Parameters page verify that the values for Name and Value are the same name and value specified in Lesson 5 for the variable and configuration value, then click Next.</span></span>  
  
9. <span data-ttu-id="1f95f-113">검토 페이지의 요악 창에서 속성을 변경하도록 설정된 구성 파일의 정보에 마법사가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f95f-113">On the Review page, in the Summary pane, notice that the wizard has used the information from the configuration file to set the Properties to be converted.</span></span>  
  
10. <span data-ttu-id="1f95f-114">변환을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f95f-114">Click Convert.</span></span>  
  
     <span data-ttu-id="1f95f-115">변환이 완료되면 프로젝트가 Visual Studio에 저장될 때까지 변경 내용이 저장되지 않음을 경고하는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f95f-115">When the conversion completes a message is displayed warning that the changes are not saved until the project is saved in Visual Studio.</span></span> <span data-ttu-id="1f95f-116">경고 대화 상자에서 확인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f95f-116">Click OK on the warning dialog.</span></span>  
  
11. <span data-ttu-id="1f95f-117">Integration Services 프로젝트 변환 마법사에서 닫기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f95f-117">On the Integration Services Project Conversion Wizard click Close.</span></span>  
  
12. <span data-ttu-id="1f95f-118">변환된 패키지를 저장하려면 SQL Server Data Tools에서 파일 메뉴를 클릭한 후 저장을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f95f-118">In SQL Server Data Tools, click the File menu, then click Save to save the converted package.</span></span>  
  
13. <span data-ttu-id="1f95f-119">매개 변수 탭을 클릭하고 패키지가 VarFolderName에 대한 매개 변수를 포함하게 되었는지 및 Lesson 5 구성 파일의 새 예제 데이터 폴더에서 지정된 것과 같은 경로의 값인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1f95f-119">Click the Parameters Tab and verify that the package now contains a parameter for VarFolderName and that the value is the same path specified for the New Sample Data folder from the Lesson 5 configuration file.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="1f95f-120">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="1f95f-120">Next Task in Lesson</span></span>  
 [<span data-ttu-id="1f95f-121">3단계: 6단원 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="1f95f-121">Step 3: Testing the Lesson 6 Package</span></span>](lesson-6-3-testing-the-lesson-6-package.md)  
  
  
