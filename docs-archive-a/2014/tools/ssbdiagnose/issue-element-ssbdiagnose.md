---
title: Issue 요소 (ssbdiagnose) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- issue element
- XML output file format [ssbdiagnose], issue element
- ssbdiagnose
ms.assetid: 2246a886-686b-44ca-9771-b155cedad8be
author: stevestein
ms.author: sstein
ms.openlocfilehash: a178c1323c1c20f84e67d4d7699fc313090a4c71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727531"
---
# <a name="issue-element-ssbdiagnose"></a><span data-ttu-id="9df6d-102">Issue 요소(ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="9df6d-102">Issue Element (ssbdiagnose)</span></span>
  <span data-ttu-id="9df6d-103">**ssbdiagnose** 유틸리티가 발견한 문제를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-103">Reports an issue that was found by the **ssbdiagnose** utility.</span></span> <span data-ttu-id="9df6d-104">**ssbdiagnose** XML 출력 파일에는 보고되는 문제 당 하나의 Issue 요소가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-104">The **ssbdiagnose** XML output file has one Issue element per issue reported.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9df6d-105">구문</span><span class="sxs-lookup"><span data-stu-id="9df6d-105">Syntax</span></span>  
  
```  
  
<Issue  
    type="..."   
    code="..."   
    server="..."   
    database="..."   
    object="...">   
    ...   
</Issue>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="9df6d-106">요소 특성</span><span class="sxs-lookup"><span data-stu-id="9df6d-106">Element Attributes</span></span>  
  
|<span data-ttu-id="9df6d-107">attribute</span><span class="sxs-lookup"><span data-stu-id="9df6d-107">Attribute</span></span>|<span data-ttu-id="9df6d-108">Description</span><span class="sxs-lookup"><span data-stu-id="9df6d-108">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="9df6d-109">Issue 요소가 보고하는 문제의 범주를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-109">Identifies which category of problem the Issue element is reporting:</span></span><br /><br /> <span data-ttu-id="9df6d-110">**"진단"** 보고서는 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 구성을 분석할 때 발견된 구성 문제를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-110">**"Diagnosis"** Reports a configuration issue found when you analyze a [!INCLUDE[ssSB](../../includes/sssb-md.md)] configuration.</span></span><br /><br /> <span data-ttu-id="9df6d-111">**"문제"** 는 **ssbdiagnose** 의 분석을 완료하지 못하게 하는 문제를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-111">**"Problem"** Reports an issue that has prevented **ssbdiagnose** from completing its analysis.</span></span> <span data-ttu-id="9df6d-112">문제를 해결하고 **ssbdiagnose**를 다시 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="9df6d-112">Correct the problem and rerun **ssbdiagnose**.</span></span><br /><br /> <span data-ttu-id="9df6d-113">**"이벤트"** 는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] -RUNTIME **검사를 실행할 때 발견된** 이벤트를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-113">**"Event"** Reports a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] event found when you run a **-RUNTIME** check.</span></span> <span data-ttu-id="9df6d-114">단, **-SHOWEVENTS** 가 지정된 경우에만 이벤트가 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-114">Events are only reported if **-SHOWEVENTS** is specified.</span></span>|  
|`code`|<span data-ttu-id="9df6d-115">메시지의 오류 번호를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-115">Identifies the error number for the message.</span></span>|  
|`server`|<span data-ttu-id="9df6d-116">문제가 발견된 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-116">Identifies the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in which the problem was found.</span></span> <span data-ttu-id="9df6d-117">문제가 기본 인스턴스에서 발견된 경우에는 서버 특성에 컴퓨터 이름만 포함되고</span><span class="sxs-lookup"><span data-stu-id="9df6d-117">If the problem was in a default instance, the server attribute only has the computer name.</span></span> <span data-ttu-id="9df6d-118">문제가 명명된 인스턴스에서 발견된 경우에는 서버 특성이 ComputerName\InstanceName 형식으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-118">If the problem was in a named instance, the server attribute is in the form ComputerName\InstanceName.</span></span>|  
|`database`|<span data-ttu-id="9df6d-119">문제가 발견된 데이터베이스의 이름을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-119">Identifies the name of the database in which the problem was found.</span></span>|  
|`object`|<span data-ttu-id="9df6d-120">문제가 발견된 개체의 이름을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-120">Identifies the name of the object in which the problem was found.</span></span> <span data-ttu-id="9df6d-121">문제가 인스턴스 또는 데이터베이스 수준에서 발견된 경우 개체 특성이 인스턴스 또는 데이터베이스 이름을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-121">If the problem was an instance or database level issue, the object attribute repeats the instance or database name.</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="9df6d-122">요소 특징</span><span class="sxs-lookup"><span data-stu-id="9df6d-122">Element Characteristics</span></span>  
  
|<span data-ttu-id="9df6d-123">특성</span><span class="sxs-lookup"><span data-stu-id="9df6d-123">Characteristic</span></span>|<span data-ttu-id="9df6d-124">Description</span><span class="sxs-lookup"><span data-stu-id="9df6d-124">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="9df6d-125">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="9df6d-125">**Data type and length**</span></span>|<span data-ttu-id="9df6d-126">`string`, 길이 제한 없음</span><span class="sxs-lookup"><span data-stu-id="9df6d-126">`string`, length is unlimited.</span></span>|  
|<span data-ttu-id="9df6d-127">**값**</span><span class="sxs-lookup"><span data-stu-id="9df6d-127">**Value**</span></span>|<span data-ttu-id="9df6d-128">오류 메시지 텍스트를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-128">Returns the text of the error message.</span></span>|  
|<span data-ttu-id="9df6d-129">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="9df6d-129">**Occurrence**</span></span>|<span data-ttu-id="9df6d-130">보고되는 오류 당 한 번</span><span class="sxs-lookup"><span data-stu-id="9df6d-130">Once per reported error.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="9df6d-131">요소 관계</span><span class="sxs-lookup"><span data-stu-id="9df6d-131">Element Relationships</span></span>  
  
|<span data-ttu-id="9df6d-132">관계</span><span class="sxs-lookup"><span data-stu-id="9df6d-132">Relationship</span></span>|<span data-ttu-id="9df6d-133">요소</span><span class="sxs-lookup"><span data-stu-id="9df6d-133">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="9df6d-134">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="9df6d-134">**Parent element**</span></span>|[<span data-ttu-id="9df6d-135">DiagnosticInformation 요소&#40;ssbdiagnose&#41;</span><span class="sxs-lookup"><span data-stu-id="9df6d-135">DiagnosticInformation Element &#40;ssbdiagnose&#41;</span></span>](diagnosticinformation-element-ssbdiagnose.md)|  
|<span data-ttu-id="9df6d-136">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="9df6d-136">**Child elements**</span></span>|<span data-ttu-id="9df6d-137">None</span><span class="sxs-lookup"><span data-stu-id="9df6d-137">None</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9df6d-138">예제</span><span class="sxs-lookup"><span data-stu-id="9df6d-138">Example</span></span>  
 <span data-ttu-id="9df6d-139">이 요소는 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 구성을 분석할 때 오류가 발견되었으며 마스터 키가 없는 데이터베이스에 대해 1102 오류를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="9df6d-139">This element reports an 1102 error for a database that does not have a master key, where the error was found when you analyzed a [!INCLUDE[ssSB](../../includes/sssb-md.md)] configuration.</span></span>  
  
```  
<Issue type="Diagnosis" code="1102" server="TestComputer" database="TargetDB" object="TargetDB">The master key was not found</diagnostic>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9df6d-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9df6d-140">See Also</span></span>  
 [<span data-ttu-id="9df6d-141">ssbdiagnose 유틸리티&#40;Service Broker&#41;</span><span class="sxs-lookup"><span data-stu-id="9df6d-141">ssbdiagnose Utility &#40;Service Broker&#41;</span></span>](ssbdiagnose-utility-service-broker.md)  
  
  
