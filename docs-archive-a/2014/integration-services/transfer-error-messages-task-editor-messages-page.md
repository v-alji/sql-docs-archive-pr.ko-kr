---
title: 오류 메시지 전송 태스크 편집기 (메시지 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfererrormessagestask.errormessages.F1
helpviewer_keywords:
- Transfer Error Messages Task Editor
ms.assetid: cb2226a0-3037-4fdf-966f-81eabc0da9cf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a0d626f01e05a30777810b26880da5aedc3e7ad3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661720"
---
# <a name="transfer-error-messages-task-editor-messages-page"></a><span data-ttu-id="23ee6-102">오류 메시지 전송 태스크 편집기(메시지 페이지)</span><span class="sxs-lookup"><span data-stu-id="23ee6-102">Transfer Error Messages Task Editor (Messages Page)</span></span>
  <span data-ttu-id="23ee6-103">**오류 메시지 전송 태스크 편집기** 대화 상자의 **메시지** 페이지를 사용하여 하나 이상의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 사용자 정의 오류 메시지를 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 한 인스턴스에서 다른 인스턴스로 복사하기 위한 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ee6-103">Use the **Messages** page of the **Transfer Error Messages Task Editor** dialog box to specify properties for copying one or more [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] user-defined error messages from one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to another.</span></span> <span data-ttu-id="23ee6-104">이 태스크에 대한 자세한 내용은 [Transfer Error Messages Task](control-flow/transfer-error-messages-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="23ee6-104">For more information about this task, see [Transfer Error Messages Task](control-flow/transfer-error-messages-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="23ee6-105">옵션</span><span class="sxs-lookup"><span data-stu-id="23ee6-105">Options</span></span>  
 <span data-ttu-id="23ee6-106">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="23ee6-106">**SourceConnection**</span></span>  
 <span data-ttu-id="23ee6-107">목록에서 SMO 연결 관리자를 선택하거나, **\<New connection...>** 을 클릭하여 원본 서버에 대한 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="23ee6-107">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="23ee6-108">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="23ee6-108">**DestinationConnection**</span></span>  
 <span data-ttu-id="23ee6-109">목록에서 SMO 연결 관리자를 선택하거나, **\<New connection...>** 을 클릭하여 대상 서버에 대한 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="23ee6-109">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="23ee6-110">**IfObjectExists**</span><span class="sxs-lookup"><span data-stu-id="23ee6-110">**IfObjectExists**</span></span>  
 <span data-ttu-id="23ee6-111">이름이 동일한 오류 메시지가 이미 대상 서버에 있는 경우 기존 사용자 정의 오류 메시지를 덮어쓸지, 기존 메시지를 건너뛸지, 아니면 태스크가 실패하도록 할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="23ee6-111">Select whether the task should overwrite existing user-defined error messages, skip existing messages, or fail if error messages of the same name already exist on the destination server.</span></span>  
  
 <span data-ttu-id="23ee6-112">**TransferAllErrorMessages**</span><span class="sxs-lookup"><span data-stu-id="23ee6-112">**TransferAllErrorMessages**</span></span>  
 <span data-ttu-id="23ee6-113">원본 서버에서 대상 서버로 모든 사용자 정의 메시지를 복사할지, 아니면 지정한 사용자 정의 메시지만 복사할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="23ee6-113">Select whether the task should copy all or only the specified user-defined messages from the source server to the destination server.</span></span>  
  
 <span data-ttu-id="23ee6-114">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ee6-114">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="23ee6-115">값</span><span class="sxs-lookup"><span data-stu-id="23ee6-115">Value</span></span>|<span data-ttu-id="23ee6-116">Description</span><span class="sxs-lookup"><span data-stu-id="23ee6-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="23ee6-117">**True**</span><span class="sxs-lookup"><span data-stu-id="23ee6-117">**True**</span></span>|<span data-ttu-id="23ee6-118">모든 사용자 정의 메시지를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="23ee6-118">Copy all user-defined messages.</span></span>|  
|<span data-ttu-id="23ee6-119">**False**</span><span class="sxs-lookup"><span data-stu-id="23ee6-119">**False**</span></span>|<span data-ttu-id="23ee6-120">지정한 사용자 정의 메시지만 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="23ee6-120">Copy only the specified user-defined messages.</span></span>|  
  
 <span data-ttu-id="23ee6-121">**ErrorMessagesList**</span><span class="sxs-lookup"><span data-stu-id="23ee6-121">**ErrorMessagesList**</span></span>  
 <span data-ttu-id="23ee6-122">복사할 오류 메시지를 선택하려면 찾아보기 단추 **(…)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23ee6-122">Click the browse button **(...)** to select the error messages to copy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="23ee6-123">복사할 오류 메시지를 선택하려면 **SourceConnection** 을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ee6-123">You must specify the **SourceConnection** before you can select error messages to copy.</span></span>  
  
 <span data-ttu-id="23ee6-124">**ErrorMessageLanguagesList**</span><span class="sxs-lookup"><span data-stu-id="23ee6-124">**ErrorMessageLanguagesList**</span></span>  
 <span data-ttu-id="23ee6-125">사용자 정의 오류 메시지를 대상 서버로 복사할 언어를 선택하려면 찾아보기 단추 **(…)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="23ee6-125">Click the browse button **(...)** to select the languages for which to copy user-defined error messages to the destination server.</span></span> <span data-ttu-id="23ee6-126">다른 언어 버전의 메시지를 대상 서버로 전송하려면 us_english(코드 페이지 1033) 버전의 메시지가 해당 서버에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ee6-126">A us_english (code page 1033) version of the message must exist on the destination server before you can transfer other language versions of the message to that server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="23ee6-127">복사할 오류 메시지를 선택하려면 **SourceConnection** 을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ee6-127">You must specify the **SourceConnection** before you can select error messages to copy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23ee6-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="23ee6-128">See Also</span></span>  
 <span data-ttu-id="23ee6-129">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="23ee6-129">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="23ee6-130">[Integration Services 태스크](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="23ee6-130">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="23ee6-131">[오류 메시지 전송 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="23ee6-131">[Transfer Error Messages Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="23ee6-132">[SMO 연결 관리자](connection-manager/smo-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="23ee6-132">[SMO Connection Manager](connection-manager/smo-connection-manager.md) </span></span>  
 <span data-ttu-id="23ee6-133">[오류 메시지 전송 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="23ee6-133">[Transfer Error Messages Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="23ee6-134">SMO 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="23ee6-134">SMO Connection Manager</span></span>](connection-manager/smo-connection-manager.md)  
  
  
