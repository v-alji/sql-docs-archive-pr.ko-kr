---
title: 감사 변환 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.audittrans.f1
helpviewer_keywords:
- environment data in packages [Integration Services]
- Audit transformation
ms.assetid: 8c143682-9c81-4150-83d6-1d9678151d37
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e8e302f6dd1dc5666ae65af2eb9705a4922915c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728512"
---
# <a name="audit-transformation"></a><span data-ttu-id="5251c-102">감사 변환</span><span class="sxs-lookup"><span data-stu-id="5251c-102">Audit Transformation</span></span>
  <span data-ttu-id="5251c-103">감사 변환을 사용하면 패키지가 실행되는 환경에 대한 데이터를 패키지의 데이터 흐름에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5251c-103">The Audit transformation enables the data flow in a package to include data about the environment in which the package runs.</span></span> <span data-ttu-id="5251c-104">예를 들어 패키지, 컴퓨터 및 운영자의 이름을 데이터 흐름에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5251c-104">For example, the name of the package, computer, and operator can be added to the data flow.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="5251c-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]는 이 정보를 제공하는 시스템 변수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5251c-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] includes system variables that provide this information.</span></span>  
  
## <a name="system-variables"></a><span data-ttu-id="5251c-106">시스템 변수</span><span class="sxs-lookup"><span data-stu-id="5251c-106">System Variables</span></span>  
 <span data-ttu-id="5251c-107">다음 표에서는 감사 변환에 사용할 수 있는 시스템 변수를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5251c-107">The following table describes the system variables that the Audit transformation can use.</span></span>  
  
|<span data-ttu-id="5251c-108">시스템 변수</span><span class="sxs-lookup"><span data-stu-id="5251c-108">System variable</span></span>|<span data-ttu-id="5251c-109">인덱스</span><span class="sxs-lookup"><span data-stu-id="5251c-109">Index</span></span>|<span data-ttu-id="5251c-110">Description</span><span class="sxs-lookup"><span data-stu-id="5251c-110">Description</span></span>|  
|---------------------|-----------|-----------------|  
|`ExecutionInstanceGUID`|<span data-ttu-id="5251c-111">0</span><span class="sxs-lookup"><span data-stu-id="5251c-111">0</span></span>|<span data-ttu-id="5251c-112">패키지의 실행 인스턴스를 식별하는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="5251c-112">The GUID that identifies the execution instance of the package.</span></span>|  
|`PackageID`|<span data-ttu-id="5251c-113">1</span><span class="sxs-lookup"><span data-stu-id="5251c-113">1</span></span>|<span data-ttu-id="5251c-114">패키지의 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="5251c-114">The unique identifier of the package.</span></span>|  
|`PackageName`|<span data-ttu-id="5251c-115">2</span><span class="sxs-lookup"><span data-stu-id="5251c-115">2</span></span>|<span data-ttu-id="5251c-116">패키지 이름.</span><span class="sxs-lookup"><span data-stu-id="5251c-116">The package name.</span></span>|  
|`VersionID`|<span data-ttu-id="5251c-117">3</span><span class="sxs-lookup"><span data-stu-id="5251c-117">3</span></span>|<span data-ttu-id="5251c-118">패키지 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="5251c-118">The version of the package.</span></span>|  
|`ExecutionStartTime`|<span data-ttu-id="5251c-119">4</span><span class="sxs-lookup"><span data-stu-id="5251c-119">4</span></span>|<span data-ttu-id="5251c-120">패키지 실행 시작 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="5251c-120">The time the package started to run.</span></span>|  
|`MachineName`|<span data-ttu-id="5251c-121">5</span><span class="sxs-lookup"><span data-stu-id="5251c-121">5</span></span>|<span data-ttu-id="5251c-122">컴퓨터 이름</span><span class="sxs-lookup"><span data-stu-id="5251c-122">The computer name.</span></span>|  
|`UserName`|<span data-ttu-id="5251c-123">6</span><span class="sxs-lookup"><span data-stu-id="5251c-123">6</span></span>|<span data-ttu-id="5251c-124">패키지를 시작한 사용자의 로그인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5251c-124">The login name of the person who started the package.</span></span>|  
|`TaskName`|<span data-ttu-id="5251c-125">7</span><span class="sxs-lookup"><span data-stu-id="5251c-125">7</span></span>|<span data-ttu-id="5251c-126">감사 변환이 연결된 데이터 흐름 태스크 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5251c-126">The name of the Data Flow task with which the Audit transformation is associated.</span></span>|  
|<span data-ttu-id="5251c-127">**TaskId**</span><span class="sxs-lookup"><span data-stu-id="5251c-127">**TaskId**</span></span>|<span data-ttu-id="5251c-128">8</span><span class="sxs-lookup"><span data-stu-id="5251c-128">8</span></span>|<span data-ttu-id="5251c-129">데이터 흐름 태스크의 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="5251c-129">The unique identifier of the Data Flow task.</span></span>|  
  
## <a name="configuration-of-the-audit-transformation"></a><span data-ttu-id="5251c-130">감사 변환 구성</span><span class="sxs-lookup"><span data-stu-id="5251c-130">Configuration of the Audit Transformation</span></span>  
 <span data-ttu-id="5251c-131">변환 출력에 추가할 새 출력 열의 이름을 지정한 다음 해당 시스템 변수를 출력 열에 매핑하여 감사 변환을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="5251c-131">You configure the Audit transformation by providing the name of a new output column to add to the transformation output, and then mapping the system variable to the output column.</span></span> <span data-ttu-id="5251c-132">단일 시스템 변수를 여러 개의 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5251c-132">You can map a single system variable to multiple columns.</span></span>  
  
 <span data-ttu-id="5251c-133">이 변환은 하나의 입력과 하나의 출력을 가지며</span><span class="sxs-lookup"><span data-stu-id="5251c-133">This transformation has one input and one output.</span></span> <span data-ttu-id="5251c-134">오류 출력은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5251c-134">It does not support an error output.</span></span>  
  
 <span data-ttu-id="5251c-135">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5251c-135">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="5251c-136">**감사 변환 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용은 [Audit Transformation Editor](../../audit-transformation-editor.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5251c-136">For more information about the properties that you can set in the **Audit Transformation Editor** dialog box, see [Audit Transformation Editor](../../audit-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="5251c-137">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5251c-137">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="5251c-138">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="5251c-138">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="5251c-139">Common Properties</span><span class="sxs-lookup"><span data-stu-id="5251c-139">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="5251c-140">변환 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="5251c-140">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="5251c-141">속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](../set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5251c-141">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
