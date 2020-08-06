---
title: SQL Server 데이터베이스 엔진 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server]
- SQL Server Database Engine
ms.assetid: 65e2f424-1386-45a6-8912-bd053f434073
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a6c243115e940f7af085c0068d2ca5c277aa5162
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646609"
---
# <a name="sql-server-database-engine"></a><span data-ttu-id="08c55-102">SQL Server 데이터베이스 엔진</span><span class="sxs-lookup"><span data-stu-id="08c55-102">SQL Server Database Engine</span></span>
  <span data-ttu-id="08c55-103">[!INCLUDE[ssDE](../includes/ssde-md.md)] 은 데이터 저장, 처리 및 보안 유지를 위한 핵심 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="08c55-103">The [!INCLUDE[ssDE](../includes/ssde-md.md)] is the core service for storing, processing, and securing data.</span></span> <span data-ttu-id="08c55-104">[!INCLUDE[ssDE](../includes/ssde-md.md)] 에서는 기업 내에서 가장 다루기 어려운 데이터 소비형 애플리케이션에 대한 요구 사항을 충족하기 위해 액세스 제어 및 빠른 트랜잭션 처리를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="08c55-104">The [!INCLUDE[ssDE](../includes/ssde-md.md)] provides controlled access and rapid transaction processing to meet the requirements of the most demanding data consuming applications within your enterprise.</span></span>

 <span data-ttu-id="08c55-105">[!INCLUDE[ssDE](../includes/ssde-md.md)] 을 사용하여 OLTP(온라인 트랜잭션 처리) 또는 OLAP(온라인 분석 처리) 데이터에 사용할 관계형 데이터베이스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08c55-105">Use the [!INCLUDE[ssDE](../includes/ssde-md.md)] to create relational databases for online transaction processing or online analytical processing data.</span></span> <span data-ttu-id="08c55-106">이 과정에는 데이터를 저장할 테이블과 데이터 보기, 관리 및 보안을 위한 인덱스, 뷰, 저장 프로시저 등의 데이터베이스 개체를 만드는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="08c55-106">This includes creating tables for storing data, and database objects such as indexes, views, and stored procedures for viewing, managing, and securing data.</span></span> <span data-ttu-id="08c55-107">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 를 사용하여 데이터베이스 개체를 관리하고 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 를 사용하여 서버 이벤트를 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08c55-107">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to manage the database objects, and [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] to capture server events.</span></span>

 <span data-ttu-id="08c55-108">**영역별 콘텐츠 찾아보기** ![작은 파일 폴더 아이콘](../../2014/integration-services/media/filefolder-small.gif "작은 파일 폴더 아이콘") [새로운 기능 (데이터베이스 엔진)](whats-new-in-sql-server-2016.md)</span><span class="sxs-lookup"><span data-stu-id="08c55-108">**Browse Content by Area** ![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [What's New (Database Engine)](whats-new-in-sql-server-2016.md)</span></span>

 <span data-ttu-id="08c55-109">![작은 파일 폴더 아이콘](../../2014/integration-services/media/filefolder-small.gif "작은 파일 폴더 아이콘") [SQL Server 이전 버전과의 호환성 데이터베이스 엔진](sql-server-database-engine-backward-compatibility.md)</span><span class="sxs-lookup"><span data-stu-id="08c55-109">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [SQL Server Database Engine Backward Compatibility](sql-server-database-engine-backward-compatibility.md)</span></span>

 <span data-ttu-id="08c55-110">[이전 버전과의 호환성 SQL Server 관리 도구](../../2014/database-engine/sql-server-management-tools-backward-compatibility.md) ![작은 파일 폴더 아이콘](../../2014/integration-services/media/filefolder-small.gif "작은 파일 폴더 아이콘")</span><span class="sxs-lookup"><span data-stu-id="08c55-110">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [SQL Server Management Tools Backward Compatibility](../../2014/database-engine/sql-server-management-tools-backward-compatibility.md)</span></span>

 <span data-ttu-id="08c55-111">![작은 파일 폴더 아이콘](../../2014/integration-services/media/filefolder-small.gif "작은 파일 폴더 아이콘") [데이터베이스 기능 및 태스크](../../2014/database-engine/database-engine-features-and-tasks.md)</span><span class="sxs-lookup"><span data-stu-id="08c55-111">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Database Features and Tasks](../../2014/database-engine/database-engine-features-and-tasks.md)</span></span>

 <span data-ttu-id="08c55-112">![작은 파일 폴더 아이콘](../../2014/integration-services/media/filefolder-small.gif "작은 파일 폴더 아이콘") [기술 참조](../../2014/database-engine/technical-reference-database-engine.md)</span><span class="sxs-lookup"><span data-stu-id="08c55-112">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Technical Reference](../../2014/database-engine/technical-reference-database-engine.md)</span></span>

 <span data-ttu-id="08c55-113">![작은 파일 폴더 아이콘](../../2014/integration-services/media/filefolder-small.gif "작은 파일 폴더 아이콘") [transact-sql 참조](/sql/t-sql/language-reference)</span><span class="sxs-lookup"><span data-stu-id="08c55-113">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Transact-SQL Reference](/sql/t-sql/language-reference)</span></span>

 <span data-ttu-id="08c55-114">![작은 파일 폴더 아이콘](../../2014/integration-services/media/filefolder-small.gif "작은 파일 폴더 아이콘") [XQuery 참조](/sql/xquery/xquery-language-reference-sql-server)</span><span class="sxs-lookup"><span data-stu-id="08c55-114">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [XQuery Reference](/sql/xquery/xquery-language-reference-sql-server)</span></span>

## <a name="see-also"></a><span data-ttu-id="08c55-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="08c55-115">See Also</span></span>
 [<span data-ttu-id="08c55-116">SQL Server 리소스 센터</span><span class="sxs-lookup"><span data-stu-id="08c55-116">SQL Server Resource Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=219676)


