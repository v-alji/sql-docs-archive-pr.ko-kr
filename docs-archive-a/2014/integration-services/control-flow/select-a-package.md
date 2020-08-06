---
title: 패키지 선택 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.selectapackage.f1
helpviewer_keywords:
- Select a Package dialog box
ms.assetid: 92b47a2b-21b5-460a-885d-6cc4bb567249
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b35276791b004a011a1c2656057046be05ed6770
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638937"
---
# <a name="select-a-package"></a><span data-ttu-id="8959c-102">패키지 선택</span><span class="sxs-lookup"><span data-stu-id="8959c-102">Select a Package</span></span>
  <span data-ttu-id="8959c-103">**패키지 선택** 대화 상자를 사용하여 메시지 큐 태스크에서 수신할 메시지를 전송하는 패키지를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8959c-103">Use the **Select a Package** dialog box to specify the package from which the Message Queue task can receive messages.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="8959c-104">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="8959c-104">Static Options</span></span>  
 <span data-ttu-id="8959c-105">**위치**</span><span class="sxs-lookup"><span data-stu-id="8959c-105">**Location**</span></span>  
 <span data-ttu-id="8959c-106">패키지의 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8959c-106">Specify the location of the package.</span></span> <span data-ttu-id="8959c-107">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8959c-107">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="8959c-108">값</span><span class="sxs-lookup"><span data-stu-id="8959c-108">Value</span></span>|<span data-ttu-id="8959c-109">Description</span><span class="sxs-lookup"><span data-stu-id="8959c-109">Description</span></span>|  
|-----------|-----------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<span data-ttu-id="8959c-110">위치를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8959c-110">Set the location to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8959c-111">이 값을 선택하면 동적 옵션 **서버**, **Windows 인증 사용**, **SQL Server 인증 사용**, **사용자 이름**및 **암호**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8959c-111">Selecting this value displays the dynamic options, **Server**, **Use Windows Authentication**, **Use SQL Server Authentication**, **User name**, and **Password**.</span></span>|  
|<span data-ttu-id="8959c-112">DTSX 파일</span><span class="sxs-lookup"><span data-stu-id="8959c-112">DTSX file</span></span>|<span data-ttu-id="8959c-113">위치를 DTSX 파일로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8959c-113">Set the location to a DTSX file.</span></span> <span data-ttu-id="8959c-114">이 값을 선택하면 동적 옵션 **파일 이름**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8959c-114">Selecting this value displays the dynamic option, **File name**.</span></span>|  
  
## <a name="location-dynamic-options"></a><span data-ttu-id="8959c-115">Location 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="8959c-115">Location Dynamic Options</span></span>  
  
### <a name="location--sql-server"></a><span data-ttu-id="8959c-116">Location = SQL Server</span><span class="sxs-lookup"><span data-stu-id="8959c-116">Location = SQL Server</span></span>  
 <span data-ttu-id="8959c-117">**패키지 이름**</span><span class="sxs-lookup"><span data-stu-id="8959c-117">**Package name**</span></span>  
 <span data-ttu-id="8959c-118">지정한 서버에 저장된 패키지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8959c-118">Select a package that is stored on the specified server.</span></span>  
  
 <span data-ttu-id="8959c-119">**Server**</span><span class="sxs-lookup"><span data-stu-id="8959c-119">**Server**</span></span>  
 <span data-ttu-id="8959c-120">서버 이름을 입력하거나 목록에서 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8959c-120">Provide a server name or select a server from the list.</span></span>  
  
 <span data-ttu-id="8959c-121">**Windows 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="8959c-121">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="8959c-122">Windows 인증을 사용하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8959c-122">Click to use Windows Authentication.</span></span>  
  
 <span data-ttu-id="8959c-123">**SQL Server 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="8959c-123">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="8959c-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8959c-124">Click to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="8959c-125">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="8959c-125">**User name**</span></span>  
 <span data-ttu-id="8959c-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하는 경우 서버에 로그온할 때 사용할 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8959c-126">If using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, provide a user name to use when logging on to the server.</span></span>  
  
 <span data-ttu-id="8959c-127">**암호**</span><span class="sxs-lookup"><span data-stu-id="8959c-127">**Password**</span></span>  
 <span data-ttu-id="8959c-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하는 경우 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8959c-128">If using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, provide a password.</span></span>  
  
### <a name="location--dtsx-file"></a><span data-ttu-id="8959c-129">위치 = DTSX 파일</span><span class="sxs-lookup"><span data-stu-id="8959c-129">Location = DTSX file</span></span>  
 <span data-ttu-id="8959c-130">**파일 이름**</span><span class="sxs-lookup"><span data-stu-id="8959c-130">**File name**</span></span>  
 <span data-ttu-id="8959c-131">패키지 경로를 입력하거나 찾아보기 단추 **(...)** 를 클릭하고 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8959c-131">Provide the path of a package or click the browse button **(...)** and locate the package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8959c-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8959c-132">See Also</span></span>  
 [<span data-ttu-id="8959c-133">메시지 큐 태스크</span><span class="sxs-lookup"><span data-stu-id="8959c-133">Message Queue Task</span></span>](message-queue-task.md)  
  
  
