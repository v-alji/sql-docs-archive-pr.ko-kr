---
title: Master 저장 프로시저 전송 태스크 편집기 (일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferstoredprocedurestask.general.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: fa1abd4c-e2be-427f-be53-860e49c97227
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8a25a5c9c6ed3802e21ac522e94163ce5fb9e8c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734284"
---
# <a name="transfer-master-stored-procedures-task-editor-general-page"></a><span data-ttu-id="77c47-102">master 저장 프로시저 전송 태스크 편집기(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="77c47-102">Transfer Master Stored Procedures Task Editor (General Page)</span></span>
  <span data-ttu-id="77c47-103">**master 저장 프로시저 전송 태스크 편집기** 대화 상자의 **일반** 페이지를 사용하여 master 저장 프로시저 전송 태스크의 이름을 지정하고 해당 태스크를 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77c47-103">Use the **General** page of the **Transfer Master Stored Procedures Task Editor** dialog box to name and describe the Transfer Master Stored Procedures task.</span></span> <span data-ttu-id="77c47-104">이 태스크에 대한 자세한 내용은 [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="77c47-104">For more information about this task, see [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77c47-105">이 태스크는 **dbo** 소유의 사용자 정의 저장 프로시저만 원본 서버의 **master** 데이터베이스에서 대상 서버의 **master** 데이터베이스로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="77c47-105">This task transfers only user-defined stored procedures owned by **dbo** from a **master** database on the source server to a **master** database on the destination server.</span></span> <span data-ttu-id="77c47-106">대상 서버의 **master** 데이터베이스에서 CREATE PROCEDURE 권한을 부여받았거나 대상 서버에서 **sysadmin** 고정 서버 역할의 멤버인 사용자만 해당 데이터베이스에 저장 프로시저를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77c47-106">Users must be granted the CREATE PROCEDURE permission in the **master** database on the destination server or be members of the **sysadmin** fixed server role on the destination server to create stored procedures there.</span></span>  
  
## <a name="options"></a><span data-ttu-id="77c47-107">옵션</span><span class="sxs-lookup"><span data-stu-id="77c47-107">Options</span></span>  
 <span data-ttu-id="77c47-108">**이름**</span><span class="sxs-lookup"><span data-stu-id="77c47-108">**Name**</span></span>  
 <span data-ttu-id="77c47-109">master 저장 프로시저 전송 태스크에 사용할 고유 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="77c47-109">Type a unique name for the Transfer Master Stored Procedures task.</span></span> <span data-ttu-id="77c47-110">이 이름은 태스크 아이콘에서 레이블로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="77c47-110">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77c47-111">태스크 이름은 패키지 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77c47-111">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="77c47-112">**설명**</span><span class="sxs-lookup"><span data-stu-id="77c47-112">**Description**</span></span>  
 <span data-ttu-id="77c47-113">master 저장 프로시저 전송 태스크에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="77c47-113">Type a description of the Transfer Master Stored Procedures task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77c47-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="77c47-114">See Also</span></span>  
 <span data-ttu-id="77c47-115">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="77c47-115">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="77c47-116">[Integration Services 태스크](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="77c47-116">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="77c47-117">[Master 저장 프로시저 전송 태스크 편집기 &#40;저장 프로시저 페이지&#41;](../../2014/integration-services/transfer-master-stored-procedures-task-editor-stored-procedures-page.md) </span><span class="sxs-lookup"><span data-stu-id="77c47-117">[Transfer Master Stored Procedures Task Editor &#40;Stored Procedures Page&#41;](../../2014/integration-services/transfer-master-stored-procedures-task-editor-stored-procedures-page.md) </span></span>  
 [<span data-ttu-id="77c47-118">식 페이지</span><span class="sxs-lookup"><span data-stu-id="77c47-118">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
