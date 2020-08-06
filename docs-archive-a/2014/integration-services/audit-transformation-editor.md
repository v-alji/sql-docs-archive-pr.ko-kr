---
title: 감사 변환 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.audittransformation.f1
helpviewer_keywords:
- Audit Transformation Editor
ms.assetid: 32786a34-5870-4fde-83c7-ec74d62404b8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: af6490643a0bef60cca961dc9a0564c5f6b46484
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740240"
---
# <a name="audit-transformation-editor"></a><span data-ttu-id="4b8c0-102">감사 변환 편집기</span><span class="sxs-lookup"><span data-stu-id="4b8c0-102">Audit Transformation Editor</span></span>
  <span data-ttu-id="4b8c0-103">감사 변환을 사용하면 패키지가 실행되는 환경에 대한 데이터를 패키지의 데이터 흐름에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-103">The Audit transformation enables the data flow in a package to include data about the environment in which the package runs.</span></span> <span data-ttu-id="4b8c0-104">예를 들어 패키지, 컴퓨터 및 운영자의 이름을 데이터 흐름에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-104">For example, the name of the package, computer, and operator can be added to the data flow.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="4b8c0-105">에는 이 정보를 제공하는 시스템 변수가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-105">includes system variables that provide this information.</span></span>  
  
 <span data-ttu-id="4b8c0-106">감사 변환에 대한 자세한 내용은 [Audit Transformation](data-flow/transformations/audit-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-106">To learn more about the Audit transformation, see [Audit Transformation](data-flow/transformations/audit-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="4b8c0-107">옵션</span><span class="sxs-lookup"><span data-stu-id="4b8c0-107">Options</span></span>  
 <span data-ttu-id="4b8c0-108">**출력 열 이름**</span><span class="sxs-lookup"><span data-stu-id="4b8c0-108">**Output column name**</span></span>  
 <span data-ttu-id="4b8c0-109">감사 정보를 포함할 새 출력 열의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-109">Provide the name for a new output column that will contain the audit information.</span></span>  
  
 <span data-ttu-id="4b8c0-110">**감사 유형**</span><span class="sxs-lookup"><span data-stu-id="4b8c0-110">**Audit type**</span></span>  
 <span data-ttu-id="4b8c0-111">감사 정보를 제공할 사용 가능한 시스템 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-111">Select an available system variable to supply the audit information.</span></span>  
  
|<span data-ttu-id="4b8c0-112">값</span><span class="sxs-lookup"><span data-stu-id="4b8c0-112">Value</span></span>|<span data-ttu-id="4b8c0-113">설명</span><span class="sxs-lookup"><span data-stu-id="4b8c0-113">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4b8c0-114">**실행 인스턴스 GUID**</span><span class="sxs-lookup"><span data-stu-id="4b8c0-114">**Execution instance GUID**</span></span>|<span data-ttu-id="4b8c0-115">패키지의 실행 인스턴스를 고유하게 식별하는 GUID를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-115">Insert the GUID that uniquely identifies the execution instance of the package.</span></span>|  
|<span data-ttu-id="4b8c0-116">**패키지 ID**</span><span class="sxs-lookup"><span data-stu-id="4b8c0-116">**Package ID**</span></span>|<span data-ttu-id="4b8c0-117">패키지를 고유하게 식별하는 GUID를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-117">Insert the GUID that uniquely identifies the package.</span></span>|  
|<span data-ttu-id="4b8c0-118">**패키지 이름**</span><span class="sxs-lookup"><span data-stu-id="4b8c0-118">**Package name**</span></span>|<span data-ttu-id="4b8c0-119">패키지 이름을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-119">Insert the package name.</span></span>|  
|<span data-ttu-id="4b8c0-120">**버전 ID**</span><span class="sxs-lookup"><span data-stu-id="4b8c0-120">**Version ID**</span></span>|<span data-ttu-id="4b8c0-121">패키지 버전을 고유하게 식별하는 GUID를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-121">Insert the GUID that uniquely identifies the version of the package.</span></span>|  
|<span data-ttu-id="4b8c0-122">**실행 시작 시간**</span><span class="sxs-lookup"><span data-stu-id="4b8c0-122">**Execution start time**</span></span>|<span data-ttu-id="4b8c0-123">패키지 실행이 시작된 시간을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-123">Insert the time at which package execution started.</span></span>|  
|<span data-ttu-id="4b8c0-124">**머신 이름**</span><span class="sxs-lookup"><span data-stu-id="4b8c0-124">**Machine name**</span></span>|<span data-ttu-id="4b8c0-125">패키지가 시작된 컴퓨터 이름을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-125">Insert the name of the computer on which the package was launched.</span></span>|  
|<span data-ttu-id="4b8c0-126">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="4b8c0-126">**User name**</span></span>|<span data-ttu-id="4b8c0-127">패키지를 시작한 사용자의 로그인 이름을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-127">Insert the login name of the user who launched the package.</span></span>|  
|<span data-ttu-id="4b8c0-128">**작업 이름**</span><span class="sxs-lookup"><span data-stu-id="4b8c0-128">**Task name**</span></span>|<span data-ttu-id="4b8c0-129">감사 변환이 연결된 데이터 흐름 태스크의 이름을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-129">Insert the name of the Data Flow task with which the Audit transformation is associated.</span></span>|  
|<span data-ttu-id="4b8c0-130">**작업 ID**</span><span class="sxs-lookup"><span data-stu-id="4b8c0-130">**Task ID**</span></span>|<span data-ttu-id="4b8c0-131">감사 변환이 연결된 데이터 흐름 태스크를 고유하게 식별하는 GUID를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8c0-131">Insert the GUID that uniquely identifies the Data Flow task with which the Audit transformation is associated.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4b8c0-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b8c0-132">See Also</span></span>  
 [<span data-ttu-id="4b8c0-133">Integration Services 오류 및 메시지 참조</span><span class="sxs-lookup"><span data-stu-id="4b8c0-133">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
