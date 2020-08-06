---
title: SQL Server Compact Edition 연결 관리자 편집기 (모든 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlmobileconnection.all.f1
helpviewer_keywords:
- SQL Server Compact Connection Manager Editor
ms.assetid: f9fbff4b-c502-44b3-8e7b-398d66e82206
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4f881d63de5435426475c3aed4b666870d706b40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649587"
---
# <a name="sql-server-compact-edition-connection-manager-editor-all-page"></a><span data-ttu-id="a9709-102">SQL Server Compact Edition 연결 관리자 편집기(모든 페이지)</span><span class="sxs-lookup"><span data-stu-id="a9709-102">SQL Server Compact Edition Connection Manager Editor (All Page)</span></span>
  <span data-ttu-id="a9709-103">**SQL Server Compact Edition 연결 관리자** 대화 상자를 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 데이터베이스에 연결하기 위한 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9709-103">Use the **SQL Server Compact Edition Connection Manager** dialog box to specify properties for connecting to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
 <span data-ttu-id="a9709-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact Edition 연결 관리자에 대한 자세한 내용은 [SQL Server Compact Edition 연결 관리자](connection-manager/sql-server-compact-edition-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9709-104">To learn more about the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact Edition connection manager, see [SQL Server Compact Edition Connection Manager](connection-manager/sql-server-compact-edition-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a9709-105">옵션</span><span class="sxs-lookup"><span data-stu-id="a9709-105">Options</span></span>  
 <span data-ttu-id="a9709-106">**자동 축소 임계값**</span><span class="sxs-lookup"><span data-stu-id="a9709-106">**AutoShrink Threshold**</span></span>  
 <span data-ttu-id="a9709-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 데이터베이스에서 자동 축소 프로세스를 실행하기 전에 허용되는 사용 가능한 공간(%)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9709-107">Specify the amount of free space, as a percentage, that is allowed in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database before the autoshrink process runs.</span></span>  
  
 <span data-ttu-id="a9709-108">**기본 잠금 에스컬레이션**</span><span class="sxs-lookup"><span data-stu-id="a9709-108">**Default Lock Escalation**</span></span>  
 <span data-ttu-id="a9709-109">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 데이터베이스가 잠금 에스컬레이션 전에 획득하는 데이터베이스 잠금 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9709-109">Specify the number of database locks that the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database acquires before it tries to escalate locks.</span></span>  
  
 <span data-ttu-id="a9709-110">**기본 잠금 제한 시간**</span><span class="sxs-lookup"><span data-stu-id="a9709-110">**Default Lock Timeout**</span></span>  
 <span data-ttu-id="a9709-111">트랜잭션에서 잠금을 대기할 기본 간격(밀리초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9709-111">Specify the default interval, in milliseconds, that a transaction will wait for a lock.</span></span>  
  
 <span data-ttu-id="a9709-112">**플러시 간격**</span><span class="sxs-lookup"><span data-stu-id="a9709-112">**Flush Interval**</span></span>  
 <span data-ttu-id="a9709-113">커밋된 트랜잭션을 디스크에 플러시하는 간격(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9709-113">Specify the interval, in seconds, between committed transactions to flush data to disk.</span></span>  
  
 <span data-ttu-id="a9709-114">**로캘 ID**</span><span class="sxs-lookup"><span data-stu-id="a9709-114">**Locale Identifier**</span></span>  
 <span data-ttu-id="a9709-115">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 데이터베이스의 LCID(로캘 ID)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9709-115">Specify the Locale ID (LCID) of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
 <span data-ttu-id="a9709-116">**최대 버퍼 크기**</span><span class="sxs-lookup"><span data-stu-id="a9709-116">**Max Buffer Size**</span></span>  
 <span data-ttu-id="a9709-117">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact에서 데이터를 디스크에 플러시하기 전에 사용하는 최대 메모리 용량(KB)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9709-117">Specify the maximum amount of memory, in kilobytes, that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact uses before flushing data to disk.</span></span>  
  
 <span data-ttu-id="a9709-118">**최대 데이터베이스 크기**</span><span class="sxs-lookup"><span data-stu-id="a9709-118">**Max Database Size**</span></span>  
 <span data-ttu-id="a9709-119">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 데이터베이스의 최대 크기(MB)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9709-119">Specify the maximum size, in megabytes, of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
 <span data-ttu-id="a9709-120">**모드**</span><span class="sxs-lookup"><span data-stu-id="a9709-120">**Mode**</span></span>  
 <span data-ttu-id="a9709-121">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 데이터베이스를 열 파일 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9709-121">Specify the file mode in which to open the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span> <span data-ttu-id="a9709-122">이 속성의 기본값은 **읽기/쓰기**입니다.</span><span class="sxs-lookup"><span data-stu-id="a9709-122">The default value for this property is **Read Write**.</span></span>  
  
 <span data-ttu-id="a9709-123">다음 표에서는 모드 옵션의 4가지 값에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9709-123">The Mode option has four values, as described in the following table.</span></span>  
  
|<span data-ttu-id="a9709-124">값</span><span class="sxs-lookup"><span data-stu-id="a9709-124">Value</span></span>|<span data-ttu-id="a9709-125">Description</span><span class="sxs-lookup"><span data-stu-id="a9709-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a9709-126">**Read Only**</span><span class="sxs-lookup"><span data-stu-id="a9709-126">**Read Only**</span></span>|<span data-ttu-id="a9709-127">데이터베이스에 대한 읽기 전용 액세스 권한을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9709-127">Specifies read-only access to the database.</span></span>|  
|<span data-ttu-id="a9709-128">**읽기 쓰기**</span><span class="sxs-lookup"><span data-stu-id="a9709-128">**Read Write**</span></span>|<span data-ttu-id="a9709-129">데이터베이스에 대한 읽기/쓰기 권한을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9709-129">Specifies read/write permission to the database.</span></span>|  
|<span data-ttu-id="a9709-130">**전용**</span><span class="sxs-lookup"><span data-stu-id="a9709-130">**Exclusive**</span></span>|<span data-ttu-id="a9709-131">데이터베이스에 대한 단독 액세스 권한을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9709-131">Specifies exclusive access to the database.</span></span>|  
|<span data-ttu-id="a9709-132">**공유 읽기**</span><span class="sxs-lookup"><span data-stu-id="a9709-132">**Shared Read**</span></span>|<span data-ttu-id="a9709-133">다른 사용자가 데이터베이스를 동시에 읽을 수 있도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9709-133">Specifies that other users can read from the database at the same time.</span></span>|  
  
 <span data-ttu-id="a9709-134">**Persist Security Info**</span><span class="sxs-lookup"><span data-stu-id="a9709-134">**Persist Security Info**</span></span>  
 <span data-ttu-id="a9709-135">보안 정보를 연결 문자열의 일부로 반환할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9709-135">Specify whether security information is returned as part of the connection string.</span></span> <span data-ttu-id="a9709-136">이 옵션의 기본값은 **False**입니다.</span><span class="sxs-lookup"><span data-stu-id="a9709-136">The default value for this option is **False**.</span></span>  
  
 <span data-ttu-id="a9709-137">**임시 파일 디렉터리**</span><span class="sxs-lookup"><span data-stu-id="a9709-137">**Temp File Directory**</span></span>  
 <span data-ttu-id="a9709-138">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 임시 데이터베이스 파일의 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9709-138">Specify the location of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact temporary database file.</span></span>  
  
 <span data-ttu-id="a9709-139">**데이터 원본**</span><span class="sxs-lookup"><span data-stu-id="a9709-139">**Data Source**</span></span>  
 <span data-ttu-id="a9709-140">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 데이터베이스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9709-140">Specify the name of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
 <span data-ttu-id="a9709-141">**암호**</span><span class="sxs-lookup"><span data-stu-id="a9709-141">**Password**</span></span>  
 <span data-ttu-id="a9709-142">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 데이터베이스의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a9709-142">Enter the password for the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9709-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a9709-143">See Also</span></span>  
 <span data-ttu-id="a9709-144">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a9709-144">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="a9709-145">SQL Server Compact Edition 연결 관리자 편집기&#40;연결 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="a9709-145">SQL Server Compact Edition Connection Manager Editor &#40;Connection Page&#41;</span></span>](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
  
