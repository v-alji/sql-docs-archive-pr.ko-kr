---
title: 데이터베이스 메일 | Microsoft 문서
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- architecture [SQL Server], Database Mail
- Database Mail [SQL Server], architecture
- Database Mail [SQL Server], components
ms.assetid: 9e4563dd-4799-4b32-a78a-048ea44a44c1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 97a5a459fafd80956a2b8d31c27b86169c6fa850
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742240"
---
# <a name="database-mail"></a><span data-ttu-id="e0905-102">데이터베이스 메일</span><span class="sxs-lookup"><span data-stu-id="e0905-102">Database Mail</span></span>
  <span data-ttu-id="e0905-103">데이터베이스 메일은 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]에서 전자 메일 메시지를 보내는 엔터프라이즈 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-103">Database Mail is an enterprise solution for sending e-mail messages from the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="e0905-104">데이터베이스 메일을 사용하여 데이터베이스 애플리케이션에서 전자 메일 메시지를 사용자에게 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-104">Using Database Mail, your database applications can send e-mail messages to users.</span></span> <span data-ttu-id="e0905-105">메시지에는 쿼리 결과와 네트워크상의 리소스 파일이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-105">The messages can contain query results, and can also include files from any resource on your network.</span></span>  
  
 
  
##  <a name="benefits-of-using-database-mail"></a><a name="Benefits"></a> <span data-ttu-id="e0905-106">데이터베이스 메일 사용의 이점</span><span class="sxs-lookup"><span data-stu-id="e0905-106">Benefits of using Database Mail</span></span>  
 <span data-ttu-id="e0905-107">데이터베이스 메일은 안정성, 확장성, 보안 및 지원 가능성을 고려하여 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-107">Database Mail is designed for reliability, scalability, security, and supportability.</span></span>  
  
### <a name="reliability"></a><span data-ttu-id="e0905-108">안정성</span><span class="sxs-lookup"><span data-stu-id="e0905-108">Reliability</span></span>  
  
-   <span data-ttu-id="e0905-109">데이터베이스 메일은 표준 SMTP(Simple Mail Transfer Protocol)를 사용하여 메일을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-109">Database Mail uses the standard Simple Mail Transfer Protocol (SMTP) to send mail.</span></span> <span data-ttu-id="e0905-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 실행하는 컴퓨터에 확장 MAPI 클라이언트를 설치하지 않고 데이터베이스 메일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-110">You can use Database Mail without installing an Extended MAPI client on the computer that runs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="e0905-111">프로세스 격리.</span><span class="sxs-lookup"><span data-stu-id="e0905-111">Process isolation.</span></span> <span data-ttu-id="e0905-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 대한 영향을 최소화하기 위해 전자 메일을 배달하는 구성 요소는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]외부에서 별도의 프로세스로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-112">To minimize the impact on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the component that delivers e-mail runs outside of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], in a separate process.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="e0905-113">는 외부 프로세스가 중지되거나 실패한 경우에도 계속해서 메일 메시지를 큐에 대기시킵니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-113">will continue to queue e-mail messages even if the external process stops or fails.</span></span> <span data-ttu-id="e0905-114">지연된 메시지는 외부 프로세스 또는 SMTP 서버가 온라인 상태로 되면 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-114">The queued messages will be sent once the outside process or SMTP server comes online.</span></span>  
  
-   <span data-ttu-id="e0905-115">장애 조치(Failover) 계정.</span><span class="sxs-lookup"><span data-stu-id="e0905-115">Failover accounts.</span></span> <span data-ttu-id="e0905-116">데이터베이스 메일 프로필을 사용하면 SMTP 서버를 둘 이상 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-116">A Database Mail profile allows you to specify more than one SMTP server.</span></span> <span data-ttu-id="e0905-117">한쪽 SMTP 서버를 사용할 수 없는 경우 메일은 다른 SMTP 서버로 배달될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-117">Should an SMTP server be unavailable, mail can still be delivered to another SMTP server.</span></span>  
  
-   <span data-ttu-id="e0905-118">클러스터 지원.</span><span class="sxs-lookup"><span data-stu-id="e0905-118">Cluster support.</span></span> <span data-ttu-id="e0905-119">데이터베이스 메일은 클러스터를 인식하므로 클러스터에서 완벽하게 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-119">Database Mail is cluster-aware and is fully supported on a cluster.</span></span>  
  
### <a name="scalability"></a><span data-ttu-id="e0905-120">확장성</span><span class="sxs-lookup"><span data-stu-id="e0905-120">Scalability</span></span>  
  
-   <span data-ttu-id="e0905-121">백그라운드 배달: 데이터베이스 메일은 백그라운드(비동기) 배달 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-121">Background Delivery: Database Mail provides background, or asynchronous, delivery.</span></span> <span data-ttu-id="e0905-122">**sp_send_dbmail** 을 호출하여 메시지를 보낼 때 데이터베이스 메일은 요청을 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 큐에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-122">When you call **sp_send_dbmail** to send a message, Database Mail adds a request to a [!INCLUDE[ssSB](../../includes/sssb-md.md)] queue.</span></span> <span data-ttu-id="e0905-123">저장 프로시저가 즉시 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-123">The stored procedure returns immediately.</span></span> <span data-ttu-id="e0905-124">외부 전자 메일 구성 요소는 요청을 받아 전자 메일을 배달합니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-124">The external e-mail component receives the request and delivers the e-mail.</span></span>  
  
-   <span data-ttu-id="e0905-125">여러 프로필: 데이터베이스 메일을 사용하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 내에 여러 프로필을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-125">Multiple profiles: Database Mail allows you to create multiple profiles within a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="e0905-126">필요에 따라 메시지를 보낼 때 데이터베이스 메일이 사용하는 프로필을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-126">Optionally, you can choose the profile that Database Mail uses when you send a message.</span></span>  
  
-   <span data-ttu-id="e0905-127">여러 계정: 각 프로필에 여러 개의 장애 조치(failover) 계정을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-127">Multiple accounts: Each profile can contain multiple failover accounts.</span></span> <span data-ttu-id="e0905-128">여러 개의 전자 메일 서버를 통해 전자 메일을 배포할 때 서로 다른 계정으로 다양한 프로필을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-128">You can configure different profiles with different accounts to distribute e-mail across multiple e-mail servers.</span></span>  
  
-   <span data-ttu-id="e0905-129">64비트 호환성: 데이터베이스 메일은 64비트 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]설치에서 완전하게 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-129">64-bit compatibility: Database Mail is fully supported on 64-bit installations of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="security"></a><span data-ttu-id="e0905-130">보안</span><span class="sxs-lookup"><span data-stu-id="e0905-130">Security</span></span>  
  
-   <span data-ttu-id="e0905-131">기본적으로 해제됨: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 노출 영역을 줄이기 위해 데이터베이스 메일 저장 프로시저는 기본적으로 사용할 수 없도록 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-131">Off by default: To reduce the surface area of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Database Mail stored procedures are disabled by default.</span></span>  
  
-   <span data-ttu-id="e0905-132">메일 보안:데이터베이스 메일을 보내려면 **msdb** 데이터베이스에서 **DatabaseMailUserRole** 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-132">Mail Security:To send Database Mail, you must be a member of the **DatabaseMailUserRole** database role in the **msdb** database.</span></span>  
  
-   <span data-ttu-id="e0905-133">프로필 보안: 데이터베이스 메일은 메일 프로필에 대해 보안을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-133">Profile security: Database Mail enforces security for mail profiles.</span></span> <span data-ttu-id="e0905-134">데이터베이스 메일 프로필에 액세스할 수 있는 **msdb** 데이터베이스 사용자나 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-134">You choose the **msdb** database users or groups that have access to a Database Mail profile.</span></span> <span data-ttu-id="e0905-135">**msdb**의 특정 사용자나 모든 사용자에게 액세스 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-135">You can grant access to either specific users, or all users in **msdb**.</span></span> <span data-ttu-id="e0905-136">프라이빗 프로필은 지정된 목록의 사용자만 액세스할 수 있도록 제한되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-136">A private profile restricts access to a specified list of users.</span></span> <span data-ttu-id="e0905-137">공개 프로필은 데이터베이스의 모든 사용자가 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-137">A public profile is available to all users in a database.</span></span>  
  
-   <span data-ttu-id="e0905-138">첨부 파일 크기 관리자: 데이터베이스 메일은 첨부 파일 크기에 대해 구성 가능한 제한을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-138">Attachment size governor: Database Mail enforces a configurable limit on the attachment file size.</span></span> <span data-ttu-id="e0905-139">[sysmail_configure_sp](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql) 저장 프로시저를 사용하여 이 제한을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-139">You can change this limit by using the [sysmail_configure_sp](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql) stored procedure.</span></span>  
  
-   <span data-ttu-id="e0905-140">금지할 파일 확장명: 데이터베이스 메일은 금지할 파일 확장명 목록을 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-140">Prohibited file extensions: Database Mail maintains a list of prohibited file extensions.</span></span> <span data-ttu-id="e0905-141">사용자는 목록에 표시된 확장명의 파일을 첨부할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-141">Users cannot attach files with an extension that appears in the list.</span></span> <span data-ttu-id="e0905-142">sysmail_configure_sp를 사용하여 이 목록을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-142">You can change this list by using sysmail_configure_sp.</span></span>  
  
-   <span data-ttu-id="e0905-143">데이터베이스 메일은e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 엔진 서비스 계정에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-143">Database Mail runs under the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Engine service account.</span></span> <span data-ttu-id="e0905-144">폴더의 파일을 전자 메일에 첨부하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 엔진 계정에 파일이 들어 있는 폴더에 대한 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-144">To attach a file from a folder to an email, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] engine account should have permissions to access the folder with the file.</span></span>  
  
### <a name="supportability"></a><span data-ttu-id="e0905-145">지원 가능성</span><span class="sxs-lookup"><span data-stu-id="e0905-145">Supportability</span></span>  
  
-   <span data-ttu-id="e0905-146">통합 구성: 데이터베이스 메일은 [!INCLUDE[ssDEnoversion](../../includes/tsql-md.md)]내에서 메일 계정에 대한 정보를 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-146">Integrated configuration: Database Mail maintains the information for e-mail accounts within [!INCLUDE[ssDEnoversion](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="e0905-147">로깅.</span><span class="sxs-lookup"><span data-stu-id="e0905-147">Logging.</span></span> <span data-ttu-id="e0905-148">데이터베이스 메일은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Microsoft Windows 애플리케이션 이벤트 로그 및 **msdb** 데이터베이스의 테이블에 메일 작업을 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-148">Database Mail logs e-mail activity to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the Microsoft Windows application event log, and to tables in the **msdb** database.</span></span>  
  
-   <span data-ttu-id="e0905-149">감사: 데이터베이스 메일은 보낸 메시지와 첨부 파일의 복사본을 **msdb** 데이터베이스에 보관합니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-149">Auditing: Database Mail keeps copies of messages and attachments sent in the **msdb** database.</span></span> <span data-ttu-id="e0905-150">데이터베이스 메일 사용을 쉽게 감사하고 보존된 메시지를 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-150">You can easily audit Database Mail usage and review the retained messages.</span></span>  
  
-   <span data-ttu-id="e0905-151">HTML 지원: 데이터베이스 메일을 사용하면 HTML 형식의 전자 메일을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-151">Support for HTML: Database Mail allows you to send e-mail formatted as HTML.</span></span>  
  

  
##  <a name="database-mail-architecture"></a><a name="VisualElement"></a> <span data-ttu-id="e0905-152">데이터베이스 메일 아키텍처</span><span class="sxs-lookup"><span data-stu-id="e0905-152">Database Mail Architecture</span></span>  
 <span data-ttu-id="e0905-153">데이터베이스 메일은 Service Broker 기술을 사용하는 큐 아키텍처를 기반으로 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-153">Database Mail is designed on a queued architecture that uses service broker technologies.</span></span> <span data-ttu-id="e0905-154">사용자가 **sp_send_dbmail**을 실행하면 이 저장 프로시저는 메일 큐에 항목을 삽입하고 메일 메시지가 포함된 레코드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-154">When users execute **sp_send_dbmail**, the stored procedure inserts an item into the mail queue and creates a record that contains the e-mail message.</span></span> <span data-ttu-id="e0905-155">메일 큐에 새 항목이 삽입되면 외부 데이터베이스 메일 프로세스(DatabaseMail.exe)가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-155">Inserting the new entry in the mail queue starts the external Database Mail process (DatabaseMail.exe).</span></span> <span data-ttu-id="e0905-156">이 외부 프로세스는 전자 메일 정보를 읽고 전자 메일 메시지를 해당 전자 메일 서버로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-156">The external process reads the e-mail information and sends the e-mail message to the appropriate e-mail server or servers.</span></span> <span data-ttu-id="e0905-157">또한 보내기 작업의 결과로 상태 큐에 항목을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-157">The external process inserts an item in the Status queue for the outcome of the send operation.</span></span> <span data-ttu-id="e0905-158">상태 큐에 새 항목이 삽입되면 전자 메일 메시지의 상태를 업데이트하는 내부 저장 프로시저가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-158">Inserting the new entry in the status queue starts an internal stored procedure that updates the status of the e-mail message.</span></span> <span data-ttu-id="e0905-159">데이터베이스 메일은 보낸 전자 메일 메시지나 보내지 않은 전자 메일 메시지를 저장할 뿐만 아니라 모든 전자 메일 첨부 파일을 시스템 테이블에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-159">Besides storing the sent, or unsent, e-mail message, Database Mail also records any e-mail attachments in the system tables.</span></span> <span data-ttu-id="e0905-160">데이터베이스 메일 뷰는 문제 해결을 위해 메시지 상태를 제공하며 저장 프로시저를 통해 데이터베이스 메일 큐를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-160">Database Mail views provide the status of messages for troubleshooting, and stored procedures allow for administration of the Database Mail queue.</span></span>  
  
 <span data-ttu-id="e0905-161">![msdb에서 SMTP 메일 서버로 메시지를 보냄](../../database-engine/media/databasemail.gif "msdb에서 SMTP 메일 서버로 메시지를 보냄")</span><span class="sxs-lookup"><span data-stu-id="e0905-161">![msdb sends messages to an SMTP mail server](../../database-engine/media/databasemail.gif "msdb sends messages to an SMTP mail server")</span></span>  
  

  
##  <a name="introduction-to-database-mail-components"></a><a name="ComponentsAndConcepts"></a> <span data-ttu-id="e0905-162">데이터베이스 메일 구성 요소 소개</span><span class="sxs-lookup"><span data-stu-id="e0905-162">Introduction to Database Mail Components</span></span>  
 <span data-ttu-id="e0905-163">데이터베이스 메일은 다음 주요 구성 요소로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-163">Database Mail consists of the following main components:</span></span>  
  
-   <span data-ttu-id="e0905-164">구성 및 보안 구성 요소</span><span class="sxs-lookup"><span data-stu-id="e0905-164">Configuration and security components</span></span>  
  
     <span data-ttu-id="e0905-165">데이터베이스 메일은 **msdb** 데이터베이스에 구성 및 보안 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-165">Database Mail stores configuration and security information in the **msdb** database.</span></span> <span data-ttu-id="e0905-166">구성 및 보안 개체는 데이터베이스 메일에 사용되는 프로필과 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-166">Configuration and security objects create profiles and accounts used by Database Mail.</span></span>  
  
-   <span data-ttu-id="e0905-167">메시징 구성 요소</span><span class="sxs-lookup"><span data-stu-id="e0905-167">Messaging components</span></span>  
  
     <span data-ttu-id="e0905-168">**msdb** 데이터베이스는 메일 호스트 데이터베이스의 역할을 수행하며 데이터베이스 메일이 메일을 보낼 때 사용하는 메시징 개체를 보유합니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-168">The **msdb** database acts as the mail-host database that holds the messaging objects that Database Mail uses to send e-mail.</span></span> <span data-ttu-id="e0905-169">이러한 개체에는 **sp_send_dbmail** 저장 프로시저 및 메시지에 대한 정보를 보유하는 데이터 구조가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-169">These objects include the **sp_send_dbmail** stored procedure and the data structures that hold information about messages.</span></span>  
  
-   <span data-ttu-id="e0905-170">데이터베이스 메일 실행 파일</span><span class="sxs-lookup"><span data-stu-id="e0905-170">Database Mail executable</span></span>  
  
     <span data-ttu-id="e0905-171">데이터베이스 메일 실행 파일은 **msdb** 데이터베이스의 큐에서 읽은 메시지를 메일 서버로 보내는 외부 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-171">The Database Mail executable is an external program that reads from a queue in the **msdb** database and sends messages to e-mail servers.</span></span>  
  
-   <span data-ttu-id="e0905-172">로깅 및 감사 구성 요소</span><span class="sxs-lookup"><span data-stu-id="e0905-172">Logging and auditing components</span></span>  
  
     <span data-ttu-id="e0905-173">데이터베이스 메일은 **msdb** 데이터베이스와 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 애플리케이션 이벤트 로그에 로깅 정보를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-173">Database Mail records logging information in the **msdb** database and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application event log.</span></span>  
  
 <span data-ttu-id="e0905-174">**데이터베이스 메일을 사용하도록 에이전트 구성:**</span><span class="sxs-lookup"><span data-stu-id="e0905-174">**Configuring Agent to use Database Mail:**</span></span>  
  
 <span data-ttu-id="e0905-175">SQL Server 에이전트는 데이터베이스 메일을 사용하도록 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-175">SQL Server Agent can be configured to use Database Mail.</span></span> <span data-ttu-id="e0905-176">이는 경고 알림 및 작업 완료 자동 알림에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-176">This is required for alert notifications and automatic notification when a job completes.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="e0905-177">작업 내의 개별 작업 단계에서는 데이터베이스 메일을 사용하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 구성하지 않고 전자 메일을 보낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-177">Individual job steps within a job can also send e-mail without configuring [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to use Database Mail.</span></span> <span data-ttu-id="e0905-178">예를 들어 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 작업 단계에서는 데이터베이스 메일을 사용하여 쿼리 결과를 받는 사람 목록에 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-178">For example, a [!INCLUDE[tsql](../../../includes/tsql-md.md)] job step can use Database Mail to send the results of a query to a list of recipients.</span></span>  
  
 <span data-ttu-id="e0905-179">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 구성하여 다음과 같은 경우에 미리 지정한 운영자에게 전자 메일을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-179">You can configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to send e-mail messages to predefined operators when:</span></span>  
  
-   <span data-ttu-id="e0905-180">경고가 트리거되었을 경우.</span><span class="sxs-lookup"><span data-stu-id="e0905-180">An alert is triggered.</span></span> <span data-ttu-id="e0905-181">경고를 구성하여 발생한 특정 이벤트를 알리는 전자 메일을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-181">Alerts can be configured to send e-mail notification of specific events that occur.</span></span> <span data-ttu-id="e0905-182">예를 들어 경고를 구성하여 즉각적인 동작이 필요한 특정 데이터베이스 이벤트 또는 운영 체제 상태를 운영자에게 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-182">For example, alerts can be configured to notify an operator of a particular database event or operating system condition that may need immediate action.</span></span> <span data-ttu-id="e0905-183">경고 구성에 대한 자세한 내용은 [경고](../../ssms/agent/alerts.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0905-183">For more information about configuring alerts, see [Alerts](../../ssms/agent/alerts.md).</span></span>  
  
-   <span data-ttu-id="e0905-184">데이터베이스 백업이나 복제 이벤트와 같이 예약된 태스크가 성공하거나 실패했을 경우.</span><span class="sxs-lookup"><span data-stu-id="e0905-184">A scheduled task, such as a database backup or replication event, succeeds or fails.</span></span> <span data-ttu-id="e0905-185">예를 들어 처리하는 동안 오류가 발생했을 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 메일을 사용하여 월말에 운영자에게 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0905-185">For example, you can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Mail to notify operators if an error occurs during processing at the end of a month.</span></span>  
  
 
  
##  <a name="database-mail-component-topics"></a><a name="RelatedContent"></a> <span data-ttu-id="e0905-186">데이터베이스 메일 구성 요소 항목</span><span class="sxs-lookup"><span data-stu-id="e0905-186">Database Mail Component Topics</span></span>  
  
-   [<span data-ttu-id="e0905-187">데이터베이스 메일 구성 개체</span><span class="sxs-lookup"><span data-stu-id="e0905-187">Database Mail Configuration Objects</span></span>](database-mail-configuration-objects.md)  
  
-   [<span data-ttu-id="e0905-188">데이터베이스 메일 메시징 개체</span><span class="sxs-lookup"><span data-stu-id="e0905-188">Database Mail Messaging Objects</span></span>](database-mail-messaging-objects.md)  
  
-   [<span data-ttu-id="e0905-189">데이터베이스 메일 외부 프로그램</span><span class="sxs-lookup"><span data-stu-id="e0905-189">Database Mail External Program</span></span>](database-mail-external-program.md)  
  
-   [<span data-ttu-id="e0905-190">데이터베이스 메일 로그 및 감사</span><span class="sxs-lookup"><span data-stu-id="e0905-190">Database Mail Log and Audits</span></span>](database-mail-log-and-audits.md)  
  
-   [<span data-ttu-id="e0905-191">데이터베이스 메일을 사용하도록 SQL Server 에이전트 메일 구성</span><span class="sxs-lookup"><span data-stu-id="e0905-191">Configure SQL Server Agent Mail to Use Database Mail</span></span>](configure-sql-server-agent-mail-to-use-database-mail.md)  
  

  
  
