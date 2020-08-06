---
title: 데이터베이스 메일 외부 프로그램 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- external programs [Database Mail]
- DatabaseMail90.exe
- Database Mail [SQL Server], external programs
ms.assetid: bc124164-eb6e-4b7f-bf66-98a3113d02f7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 698fc8d97a565b4181552691a0260486c9c43bfd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742268"
---
# <a name="database-mail-external-program"></a><span data-ttu-id="edce6-102">데이터베이스 메일 외부 프로그램</span><span class="sxs-lookup"><span data-stu-id="edce6-102">Database Mail External Program</span></span>
  <span data-ttu-id="edce6-103">데이터베이스 메일 외부 프로그램의 실행 파일은 **DatabaseMail.exe**이며 **설치 위치의** MSSQL\Binn 디렉터리 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edce6-103">The Database Mail external executable is **DatabaseMail.exe**, located in the **MSSQL\Binn directory** of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="edce6-104">데이터베이스 메일은 처리할 전자 메일 메시지가 있는 경우 Service Broker 활성화를 사용하여 외부 프로그램을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="edce6-104">Database Mail uses Service Broker activation to start the external program when there are e-mail messages to be processed.</span></span> <span data-ttu-id="edce6-105">데이터베이스 메일은 외부 프로그램의 인스턴스 하나를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="edce6-105">Database Mail starts one instance of the external program.</span></span> <span data-ttu-id="edce6-106">외부 프로그램은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 대한 서비스 계정의 보안 컨텍스트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="edce6-106">The external program runs in the security context of the service account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="edce6-107">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="edce6-107">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="edce6-108">데이터베이스 메일 외부 프로그램 개념</span><span class="sxs-lookup"><span data-stu-id="edce6-108">Database Mail External Program Concepts</span></span>](#ComponentsAndConcepts)  
  
-   [<span data-ttu-id="edce6-109">데이터베이스 메일 외부 프로그램 구성 관련 태스크</span><span class="sxs-lookup"><span data-stu-id="edce6-109">Tasks Related to Configuring Database Mail External Program</span></span>](#RelatedTasks)  
  
##  <a name="database-mail-external-program-concepts"></a><a name="ComponentsAndConcepts"></a> <span data-ttu-id="edce6-110">데이터베이스 메일 외부 프로그램 개념</span><span class="sxs-lookup"><span data-stu-id="edce6-110">Database Mail External Program Concepts</span></span>  
 <span data-ttu-id="edce6-111">외부 프로그램이 시작되면 이 프로그램은 Windows 인증을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결하고 전자 메일 메시지를 처리하기 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="edce6-111">When the external program starts, the program connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Windows Authentication and begins processing e-mail messages.</span></span> <span data-ttu-id="edce6-112">지정된 제한 시간 동안 보낼 메시지가 없는 경우 프로그램이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="edce6-112">When there have been no messages to send for the specified time-out period, the program exits.</span></span> <span data-ttu-id="edce6-113">데이터베이스 메일 구성 마법사 또는 데이터베이스 메일 저장 프로시저를 사용하여 프로그램의 종료 대기 시간을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edce6-113">You can configure the amount of time that the program waits before exiting by using either Database Mail Configuration Wizard or the Database Mail stored procedures.</span></span> <span data-ttu-id="edce6-114">자세한 내용은 [sysmail_configure_sp&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql)에 대한 서비스 계정의 보안 컨텍스트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="edce6-114">For more information, see [sysmail_configure_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql).</span></span>  
  
 <span data-ttu-id="edce6-115">외부 프로그램은 **msdb** 데이터베이스의 시스템 테이블에 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="edce6-115">The external program stores information in system tables in the **msdb** database.</span></span> <span data-ttu-id="edce6-116">외부 프로그램이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 통신할 수 없는 경우 프로그램은 Microsoft Windows 애플리케이션 이벤트 로그에 오류를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="edce6-116">If the external program cannot communicate with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the program logs errors to the Microsoft Windows application event log.</span></span> <span data-ttu-id="edce6-117">**데이터베이스 메일 구성 마법사** 의 **시스템 매개 변수 구성** 대화 상자에서 로깅 수준이 **자세히**로 설정되어 있으면 추가 메시지 로깅이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="edce6-117">Additional message logging is provided when the logging level is set to **Verbose** in the **Configure System Parameters** dialog box of the **Database Mail Configuration Wizard**.</span></span>  
  
 <span data-ttu-id="edce6-118">외부 프로그램은 효율적인 처리를 위해 계정 및 프로필 정보를 캐시한다는 점에 유의하세요.</span><span class="sxs-lookup"><span data-stu-id="edce6-118">Notice that, for efficiency, the external program caches account and profile information.</span></span> <span data-ttu-id="edce6-119">그러므로 계정 및 프로필에 대한 구성 변경 내용은 몇 분 동안 외부 프로그램에 반영되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edce6-119">Therefore, configuration changes to accounts and profiles may not be reflected in the external program for a few minutes.</span></span>  
  
##  <a name="tasks-related-to-configuring-database-mail-external-program"></a><a name="RelatedTasks"></a> <span data-ttu-id="edce6-120">데이터베이스 메일 외부 프로그램 구성 관련 태스크</span><span class="sxs-lookup"><span data-stu-id="edce6-120">Tasks Related to Configuring Database Mail External Program</span></span>  
  
|<span data-ttu-id="edce6-121">구성 태스크</span><span class="sxs-lookup"><span data-stu-id="edce6-121">Configuration Task</span></span>|<span data-ttu-id="edce6-122">항목 링크</span><span class="sxs-lookup"><span data-stu-id="edce6-122">Topic Link</span></span>|  
|------------------------|----------------|  
|<span data-ttu-id="edce6-123">외부 프로그램을 종료하기 전에 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="edce6-123">Specify the time that the External Program before exiting.</span></span>|[<span data-ttu-id="edce6-124">sysmail_configure_sp&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="edce6-124">sysmail_configure_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql)|  
  
## <a name="see-also"></a><span data-ttu-id="edce6-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="edce6-125">See Also</span></span>  
 <span data-ttu-id="edce6-126">[SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md) </span><span class="sxs-lookup"><span data-stu-id="edce6-126">[SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md) </span></span>  
 <span data-ttu-id="edce6-127">[데이터베이스 메일 로그 및 감사](database-mail-log-and-audits.md) </span><span class="sxs-lookup"><span data-stu-id="edce6-127">[Database Mail Log and Audits](database-mail-log-and-audits.md) </span></span>  
 [<span data-ttu-id="edce6-128">데이터베이스 메일</span><span class="sxs-lookup"><span data-stu-id="edce6-128">Database Mail</span></span>](database-mail.md)  
  
  
