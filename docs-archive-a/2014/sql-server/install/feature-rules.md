---
title: 기능 규칙 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: f75541cb-f78d-4303-a641-d5d3d58ae1fa
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5b0906e2f2c95a42849b6a69e60d5f26153d3a6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730055"
---
# <a name="feature-rules"></a><span data-ttu-id="8731d-102">기능 규칙</span><span class="sxs-lookup"><span data-stu-id="8731d-102">Feature Rules</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8731d-103">설치 프로그램은 설치 작업이 완료되기 전에 컴퓨터 구성의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="8731d-103">Setup validates your computer configuration before the Setup operation completes.</span></span> <span data-ttu-id="8731d-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 중에 SCC(시스템 구성 검사기)는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 설치할 컴퓨터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8731d-104">During [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup, the System Configuration Checker (SCC) scans the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will be installed.</span></span> <span data-ttu-id="8731d-105">SCC는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 성공적인 설치 작업을 방해하는 조건이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8731d-105">The SCC checks for conditions that prevent a successful [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup operation.</span></span> <span data-ttu-id="8731d-106">설치 프로그램이 시작하기 전에 SCC는 각 항목의 상태를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8731d-106">Before Setup starts, the SCC retrieves the status of each item.</span></span> <span data-ttu-id="8731d-107">그런 다음 검색 결과를 필수 조건과 비교하고 차단 문제 해결을 위한 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8731d-107">It then compares the result with required conditions and provides guidance for removal of blocking issues.</span></span>  
  
 <span data-ttu-id="8731d-108">시스템 구성 검사에서는 각 실행 규칙에 대한 간단한 설명과 실행 상태를 포함하는 보고서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="8731d-108">The system configuration check generates a report which contains a short description for each executed rule, and the execution status.</span></span> <span data-ttu-id="8731d-109">시스템 구성 검사 보고서 는% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>에 있습니다 \\ .</span><span class="sxs-lookup"><span data-stu-id="8731d-109">The system configuration check report is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
 <span data-ttu-id="8731d-110">설치 작업을 실행하기 전에 다음 항목을 검토하십시오.</span><span class="sxs-lookup"><span data-stu-id="8731d-110">Before you run the setup operation, review the following topics:</span></span>  
  
1.  [<span data-ttu-id="8731d-111">SQL Server 2014 설치에 대한 하드웨어 및 소프트웨어 요구 사항</span><span class="sxs-lookup"><span data-stu-id="8731d-111">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](hardware-and-software-requirements-for-installing-sql-server.md)  
  
2.  [<span data-ttu-id="8731d-112">SQL Server 2014 버전에서 지원하는 기능</span><span class="sxs-lookup"><span data-stu-id="8731d-112">Features Supported by the Editions of SQL Server 2014</span></span>](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
3.  [<span data-ttu-id="8731d-113">SQL Server 설치에 대한 보안 고려 사항</span><span class="sxs-lookup"><span data-stu-id="8731d-113">Security Considerations for a SQL Server Installation</span></span>](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
4.  [<span data-ttu-id="8731d-114">SQL Server의 로컬 언어 버전</span><span class="sxs-lookup"><span data-stu-id="8731d-114">Local Language Versions in SQL Server</span></span>](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
  
 <span data-ttu-id="8731d-115">기타 참조:</span><span class="sxs-lookup"><span data-stu-id="8731d-115">Other references:</span></span>  
  
1.  [<span data-ttu-id="8731d-116">지원되는 버전 및 에디션 업그레이드</span><span class="sxs-lookup"><span data-stu-id="8731d-116">Supported Version and Edition Upgrades</span></span>](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
2.  [<span data-ttu-id="8731d-117">장애 조치(Failover) 클러스터링을 설치하기 전에</span><span class="sxs-lookup"><span data-stu-id="8731d-117">Before Installing Failover Clustering</span></span>](../failover-clusters/install/before-installing-failover-clustering.md)  
  
  
