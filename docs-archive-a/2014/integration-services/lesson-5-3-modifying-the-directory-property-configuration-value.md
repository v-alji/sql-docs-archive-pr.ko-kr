---
title: '3단계: Directory 속성 구성 값 수정 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ba2a091f-361c-4331-afe2-53b465164c36
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a71a7a181322d60caca98da4ddf3261cbce99c9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648430"
---
# <a name="step-3-modifying-the-directory-property-configuration-value"></a><span data-ttu-id="8e61e-102">3단계: Directory 속성 구성 값 수정</span><span class="sxs-lookup"><span data-stu-id="8e61e-102">Step 3: Modifying the Directory Property Configuration Value</span></span>
  <span data-ttu-id="8e61e-103">이 태스크에서는 패키지 수준 변수 `User::varFolderName`의 Value 속성에 대해 SSISTutorial.dtsConfig 파일에 저장된 구성 설정을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e61e-103">In this task, you will modify the configuration setting, stored in the SSISTutorial.dtsConfig file, for the Value property of the package-level variable `User::varFolderName`.</span></span> <span data-ttu-id="8e61e-104">이 변수는 Foreach 루프 컨테이너의 Directory 속성을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8e61e-104">The variable updates the Directory property of the Foreach Loop container.</span></span> <span data-ttu-id="8e61e-105">수정 된 값은 `New Sample Data` 이전 작업에서 만든 폴더를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="8e61e-105">The modified value will point to the `New Sample Data` folder that you created in the previous task.</span></span> <span data-ttu-id="8e61e-106">구성 설정을 수정하고 패키지를 실행하면 Directory 속성은 원래 패키지에서 구성된 디렉터리 값 대신 구성 파일에서 채워진 값을 사용하여 변수를 통해 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e61e-106">After you modify the configuration setting and run the package, the Directory property will be updated by the variable, using the value populated from the configuration file instead of the directory value originally configured in the package.</span></span>  
  
### <a name="to-modify-the-configuration-setting-of-the-directory-property"></a><span data-ttu-id="8e61e-107">Directory 속성의 구성 설정을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="8e61e-107">To modify the configuration setting of the Directory property</span></span>  
  
1.  <span data-ttu-id="8e61e-108">메모장이나 다른 텍스트 편집기에서 패키지 구성 마법사를 사용하여 이전 태스크에서 만든 SSISTutorial.dtsConfig 구성 파일을 찾아 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8e61e-108">In Notepad or any other text editor, locate and open the SSISTutorial.dtsConfig configuration file that you created by using the Package Configuration Wizard in the previous task.</span></span>  
  
2.  <span data-ttu-id="8e61e-109">**ConfiguredValue** 요소의 값을 `New Sample Data` 이전 작업에서 만든 폴더의 경로와 일치 하도록 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e61e-109">Change the value of the **ConfiguredValue** element to match the path of the `New Sample Data` folder that you created in the previous task.</span></span> <span data-ttu-id="8e61e-110">경로를 따옴표로 묶지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="8e61e-110">Do not surround the path in quotes.</span></span> <span data-ttu-id="8e61e-111">`New Sample Data`폴더가 드라이브의 루트 수준 (예: C:)에 있는 경우 \\ 업데이트 된 XML은 다음 샘플과 비슷해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e61e-111">If the `New Sample Data` folder is at the root level of your drive (for example, C:\\), the updated XML should be similar to the following sample:</span></span>  
  
     `<?xml version="1.0"?><DTSConfiguration><DTSConfigurationHeading><DTSConfigurationFileInfo GeneratedBy="DOMAIN\UserName" GeneratedFromPackageName="Lesson 5" GeneratedFromPackageID="{F4475E73-59E3-478F-8EB2-B10AFA61D3FA}" GeneratedDate="6/10/2012 8:16:50 AM"/></DTSConfigurationHeading><Configuration ConfiguredType="Property" Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType="String"><ConfiguredValue></ConfiguredValue></Configuration></DTSConfiguration>`  
  
     <span data-ttu-id="8e61e-112">물론 제목 정보, `GeneratedBy` , `GeneratedFromPackageID` 및 **generateddate** 는 파일에서 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="8e61e-112">The heading information, `GeneratedBy`, `GeneratedFromPackageID`, and **GeneratedDate** will be different in your file, of course.</span></span> <span data-ttu-id="8e61e-113">주의해야 할 요소는 `Configuration`입니다.</span><span class="sxs-lookup"><span data-stu-id="8e61e-113">The element to note is the `Configuration` element.</span></span> <span data-ttu-id="8e61e-114">이제 변수의 `Value` 속성인 `User::varFolderName`에 C:\New Sample Data가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e61e-114">The `Value` property of the variable, `User::varFolderName`, now contains C:\New Sample Data.</span></span>  
  
3.  <span data-ttu-id="8e61e-115">변경 내용을 저장하고 텍스트 편집기를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="8e61e-115">Save the change, and then close the text editor.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="8e61e-116">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="8e61e-116">Next Task in Lesson</span></span>  
 [<span data-ttu-id="8e61e-117">4단계: 5단원 자습서 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="8e61e-117">Step 4: Testing the Lesson 5 Tutorial Package</span></span>](../integration-services/lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
  
