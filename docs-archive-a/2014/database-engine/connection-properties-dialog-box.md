---
title: 연결 속성 대화 상자 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connectionproperties.f1
helpviewer_keywords:
- Connection Properties dialog box
ms.assetid: 6df812ad-4d80-4503-8a23-47719ce85624
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: db2817ebaf3f1655f146c060fcb79d550ad0cc8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740347"
---
# <a name="connection-properties-dialog-box"></a><span data-ttu-id="6116c-102">연결 속성 대화 상자</span><span class="sxs-lookup"><span data-stu-id="6116c-102">Connection Properties Dialog Box</span></span>
  <span data-ttu-id="6116c-103">이 대화 상자를 사용하여 현재 연결 속성을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-103">Use this dialog box to view the current connection properties.</span></span> <span data-ttu-id="6116c-104">다양한 개체 탐색기 대화 상자에서 **연결 속성 보기** 를 클릭하면 이 대화 상자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-104">This dialog box is available when you click **View connection properties** in various Object Explorer dialog boxes.</span></span> <span data-ttu-id="6116c-105">이 페이지에 표시된 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-105">The properties displayed on this page are read-only.</span></span>  
  
 <span data-ttu-id="6116c-106">**데이터베이스**와 같은 속성을 변경하려면 **연결 속성** 대화 상자를 열기 전에 개체 탐색기로 원하는 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-106">To change properties such as **Database**, connect to the desired database with Object Explorer before opening the **Connection Properties** dialog box.</span></span>  
  
 <span data-ttu-id="6116c-107">SQL Azure의 쿼리 제한 시간은 30분입니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-107">Note that the query time-out period for SQL Azure is 30 minutes.</span></span>  
  
## <a name="authentication"></a><span data-ttu-id="6116c-108">인증</span><span class="sxs-lookup"><span data-stu-id="6116c-108">Authentication</span></span>  
 <span data-ttu-id="6116c-109">현재 연결에 대한 인증 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-109">View authentication properties for the current connection.</span></span> <span data-ttu-id="6116c-110">인증 속성은 연결을 설정할 때 사용한 로그인 및 인증 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-110">Authentication properties are the login and authentication method when the connection was established.</span></span> <span data-ttu-id="6116c-111">인증 속성을 변경 하려면에서 연결을 끊은 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 다음 원하는 연결 옵션을 사용 하 여 서버에 개체 탐색기을 다시 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-111">To change the authentication properties, disconnect from [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and then connect Object Explorer to the server again, using the desired connection options.</span></span>  
  
 <span data-ttu-id="6116c-112">**인증 방법**</span><span class="sxs-lookup"><span data-stu-id="6116c-112">**Authentication Method**</span></span>  
 <span data-ttu-id="6116c-113">현재 연결에 사용된 인증 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-113">The authentication method used for the current connection.</span></span>  
  
 <span data-ttu-id="6116c-114">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="6116c-114">**User Name**</span></span>  
 <span data-ttu-id="6116c-115">연결 인증에 사용된 로그인의 사용자 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-115">The name of the user of login used for the connection authentication.</span></span>  
  
## <a name="connection-category"></a><span data-ttu-id="6116c-116">연결 범주</span><span class="sxs-lookup"><span data-stu-id="6116c-116">Connection Category</span></span>  
 <span data-ttu-id="6116c-117">현재 연결에 대한 연결 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-117">View connection properties for the current connection.</span></span> <span data-ttu-id="6116c-118">대부분의 연결 속성은 연결하는 동안 **서버에 연결** 대화 상자의 **연결 속성** 탭에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-118">Most connection properties were selected on the **Connection Properties** tab of the **Connect to server** dialog box during the connection process.</span></span>  
  
 <span data-ttu-id="6116c-119">**Database**</span><span class="sxs-lookup"><span data-stu-id="6116c-119">**Database**</span></span>  
 <span data-ttu-id="6116c-120">현재 연결된 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-120">The name of the database currently connected to.</span></span> <span data-ttu-id="6116c-121">이름을 변경하려면 SQL 편집기 도구 모음을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-121">To change this use, the SQL Editor toolbar.</span></span>  
  
 <span data-ttu-id="6116c-122">**SPID**</span><span class="sxs-lookup"><span data-stu-id="6116c-122">**SPID**</span></span>  
 <span data-ttu-id="6116c-123">서버에서 연결에 할당한 시스템 프로세스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-123">The system process ID assigned by the server to the connection.</span></span> <span data-ttu-id="6116c-124">이 연결에 대해서는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-124">This cannot be changed for this connection.</span></span>  
  
 <span data-ttu-id="6116c-125">**네트워크 프로토콜**</span><span class="sxs-lookup"><span data-stu-id="6116c-125">**Network Protocol**</span></span>  
 <span data-ttu-id="6116c-126">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 연결의 네트워크 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-126">The network protocol of the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] connection.</span></span> <span data-ttu-id="6116c-127">이를 변경하려면 원하는 연결 속성으로 다시 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-127">To change this, connect again with the desired connection properties.</span></span>  
  
 <span data-ttu-id="6116c-128">**네트워크 패킷 크기**</span><span class="sxs-lookup"><span data-stu-id="6116c-128">**Network Packet Size**</span></span>  
 <span data-ttu-id="6116c-129">서버와 통신할 때 사용되는 패킷 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-129">The packet size used when communicating with the server.</span></span> <span data-ttu-id="6116c-130">이를 변경하려면 원하는 연결 속성으로 다시 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-130">To change this, connect again with the desired connection properties.</span></span>  
  
 <span data-ttu-id="6116c-131">**연결 시간 제한**</span><span class="sxs-lookup"><span data-stu-id="6116c-131">**Connection Timeout**</span></span>  
 <span data-ttu-id="6116c-132">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에 연결할 때 대기하는 시간(초)입니다. 이 시간이 지나면 사용자에게 연결 실패 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-132">The amount of time is seconds to wait when connecting to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] before timing out and returning a failure to connect error to the user.</span></span> <span data-ttu-id="6116c-133">이를 변경하려면 원하는 연결 속성으로 다시 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-133">To change this, connect again with the desired connection properties.</span></span>  
  
 <span data-ttu-id="6116c-134">**실행 제한 시간**</span><span class="sxs-lookup"><span data-stu-id="6116c-134">**Execution Timeout**</span></span>  
 <span data-ttu-id="6116c-135">서버에서 태스크 실행이 완료되기까지 대기하는 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-135">The amount of time in seconds to wait before execution of a task is completed on the server.</span></span> <span data-ttu-id="6116c-136">이를 변경하려면 원하는 연결 속성으로 다시 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-136">To change this, connect again with the desired connection properties.</span></span>  
  
 <span data-ttu-id="6116c-137">**암호화됨**</span><span class="sxs-lookup"><span data-stu-id="6116c-137">**Encrypted**</span></span>  
 <span data-ttu-id="6116c-138">현재 연결의 암호화 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-138">Whether the current connection is encrypted.</span></span> <span data-ttu-id="6116c-139">이를 변경하려면 원하는 연결 속성으로 다시 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-139">To change this, connect again with the desired connection properties.</span></span>  
  
## <a name="product-category"></a><span data-ttu-id="6116c-140">제품 범주</span><span class="sxs-lookup"><span data-stu-id="6116c-140">Product Category</span></span>  
 <span data-ttu-id="6116c-141">현재 연결에 대한 제품 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-141">View product properties for the current connection.</span></span> <span data-ttu-id="6116c-142">이러한 속성은 서버 제품, 버전, 인스턴스 이름 및 데이터 정렬에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-142">These properties describe the server product, version, instance name, and collation.</span></span> <span data-ttu-id="6116c-143">속성은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 설치 과정에서 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-143">The properties are set during [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] installation.</span></span>  
  
 <span data-ttu-id="6116c-144">**제품 이름**</span><span class="sxs-lookup"><span data-stu-id="6116c-144">**Product Name**</span></span>  
 <span data-ttu-id="6116c-145">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 제품 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-145">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] product name.</span></span>  
  
 <span data-ttu-id="6116c-146">**제품 버전**</span><span class="sxs-lookup"><span data-stu-id="6116c-146">**Product Version**</span></span>  
 <span data-ttu-id="6116c-147">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 제품 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-147">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] product version.</span></span>  
  
 <span data-ttu-id="6116c-148">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="6116c-148">**Server Name**</span></span>  
 <span data-ttu-id="6116c-149">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]를 실행 중인 컴퓨터의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-149">The name of the computer running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="6116c-150">**인스턴스 이름**</span><span class="sxs-lookup"><span data-stu-id="6116c-150">**Instance Name**</span></span>  
 <span data-ttu-id="6116c-151">서버의 인스턴스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-151">The instance name of the server.</span></span> <span data-ttu-id="6116c-152">기본 인스턴스는 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-152">The default instance is blank.</span></span>  
  
 <span data-ttu-id="6116c-153">**언어**</span><span class="sxs-lookup"><span data-stu-id="6116c-153">**Language**</span></span>  
 <span data-ttu-id="6116c-154">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 제품의 언어 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-154">The language version of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] product.</span></span>  
  
 <span data-ttu-id="6116c-155">**데이터 정렬**</span><span class="sxs-lookup"><span data-stu-id="6116c-155">**Collation**</span></span>  
 <span data-ttu-id="6116c-156">서버의 데이터 정렬입니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-156">The collation of the server.</span></span>  
  
## <a name="server-environment-category"></a><span data-ttu-id="6116c-157">서버 환경 범주</span><span class="sxs-lookup"><span data-stu-id="6116c-157">Server Environment Category</span></span>  
 <span data-ttu-id="6116c-158">현재 연결의 서버 하드웨어 및 운영 체제와 관련된 서버 환경 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-158">View server environment properties for the current connection related to the server hardware and operating system.</span></span> <span data-ttu-id="6116c-159">이러한 속성은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-159">The properties cannot be configured by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="6116c-160">**컴퓨터 이름**</span><span class="sxs-lookup"><span data-stu-id="6116c-160">**Computer Name**</span></span>  
 <span data-ttu-id="6116c-161">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]를 실행 중인 서버 컴퓨터의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-161">The name of the server computer that is running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="6116c-162">**플랫폼**</span><span class="sxs-lookup"><span data-stu-id="6116c-162">**Platform**</span></span>  
 <span data-ttu-id="6116c-163">서버의 운영 체제 이름, 제조업체 이름 및 CPU 제품군입니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-163">The operating system name, manufacturer name, and CPU family of the server.</span></span>  
  
 <span data-ttu-id="6116c-164">**운영 체제**</span><span class="sxs-lookup"><span data-stu-id="6116c-164">**Operating System**</span></span>  
 <span data-ttu-id="6116c-165">서버에 설치되어 있는 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-165">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows version installed on the server.</span></span>  
  
 <span data-ttu-id="6116c-166">**프로세서**</span><span class="sxs-lookup"><span data-stu-id="6116c-166">**Processors**</span></span>  
 <span data-ttu-id="6116c-167">서버의 프로세서 수입니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-167">The number of processors on the server.</span></span>  
  
 <span data-ttu-id="6116c-168">**운영 체제 메모리**</span><span class="sxs-lookup"><span data-stu-id="6116c-168">**Operating System Memory**</span></span>  
 <span data-ttu-id="6116c-169">서버의 실제 메모리 전체 크기(MB)입니다.</span><span class="sxs-lookup"><span data-stu-id="6116c-169">The total amount of physical memory on the server, in megabytes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6116c-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6116c-170">See Also</span></span>  
 <span data-ttu-id="6116c-171">[SQL Server Management Studio의 속성 페이지](../ssms/property-pages-in-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="6116c-171">[Property Pages in SQL Server Management Studio](../ssms/property-pages-in-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="6116c-172">서버에 연결&#40;로그인 페이지&#41; 데이터베이스 엔진</span><span class="sxs-lookup"><span data-stu-id="6116c-172">Connect to Server &#40;Login Page&#41; Database Engine</span></span>](../ssms/f1-help/connect-to-server-login-page-database-engine.md)  
  
  
