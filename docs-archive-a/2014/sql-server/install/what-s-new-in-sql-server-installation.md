---
title: SQL Server 설치의 새로운 기능 | Microsoft 문서
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, what's new
- SQL Server, what's new
- SQL Server, installing
ms.assetid: c8642a96-3a09-4ec7-a9c3-c539147e6330
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d34085e320cd8ca0b82d382d6d49eaa303086114
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650385"
---
# <a name="what39s-new-in-sql-server-installation"></a><span data-ttu-id="fbc71-102">SQL Server 설치의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="fbc71-102">What&#39;s New in SQL Server Installation</span></span>
  <span data-ttu-id="fbc71-103">Windows Vista는 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]에서 지원되는 운영 체제가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="fbc71-103">Windows Vista is not a supported operating system for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].</span></span> <span data-ttu-id="fbc71-104">[!INCLUDE[win7](../../includes/win7-md.md)] 및 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 운영 체제의 경우에는 최소 요구 사항이 서비스 팩 1입니다.</span><span class="sxs-lookup"><span data-stu-id="fbc71-104">Service Pack 1 remains as the minimum requirement for [!INCLUDE[win7](../../includes/win7-md.md)] and [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] operating systems.</span></span> <span data-ttu-id="fbc71-105">운영 체제 요구 사항에 대 한 자세한 내용은 [SQL Server 2014을 설치 하기 위한 하드웨어 및 소프트웨어 요구 사항](hardware-and-software-requirements-for-installing-sql-server.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fbc71-105">For more information on operating system requirements, see [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
 <span data-ttu-id="fbc71-106">[!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] 를 설치하면 압축을 푼 패키지를 저장할 디렉터리를 지정하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbc71-106">Installation of [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] will prompt you to specify the directory to save the extracted package.</span></span> <span data-ttu-id="fbc71-107">위치를 입력하지 않으면 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]에서 기본적으로 컴퓨터의 시스템 드라이브가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbc71-107">If no location is entered, [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] will default to the computer's system drive.</span></span> <span data-ttu-id="fbc71-108">압축을 푼 파일은 [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] 설치가 완료된 뒤에도 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbc71-108">The extracted files will remain after [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] installation is complete.</span></span>  
  
 <span data-ttu-id="fbc71-109">[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]에서는 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치에 SysPrep이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbc71-109">In [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], SysPrep is supported for all installations of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fbc71-110">이제 장애 조치(Failover) 클러스터 설치에 SysPrep이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbc71-110">SysPrep now supports failover cluster installations.</span></span> <span data-ttu-id="fbc71-111">자세한 내용은 [sysprep을 사용 하 여 SQL Server 설치에 대 한 고려 사항](../../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md) 및 [Sysprep을 사용 하 여 SQL Server 2014 설치](../../database-engine/install-windows/install-sql-server-using-sysprep.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fbc71-111">For more information, see [Considerations for Installing SQL Server Using SysPrep](../../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md) and [Install SQL Server 2014 Using SysPrep](../../database-engine/install-windows/install-sql-server-using-sysprep.md).</span></span>  
  
 <span data-ttu-id="fbc71-112">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서의 업그레이드는 지원되지만 함께 설치는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fbc71-112">Upgrade from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] is supported, but side-by-side is not supported.</span></span> <span data-ttu-id="fbc71-113">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 의 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]지원에 대한 자세한 내용은 [지원되는 버전 및 버전 업그레이드](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fbc71-113">For more information about [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] support in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], see [Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md).</span></span>  
  
 <span data-ttu-id="fbc71-114">[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]부터 Standard 버전의 데이터베이스 엔진에 대한 메모리 용량은 128GB입니다.</span><span class="sxs-lookup"><span data-stu-id="fbc71-114">Beginning in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], the database engine in the Standard edition has a memory capacity of 128 GB.</span></span> <span data-ttu-id="fbc71-115">에서 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Standard 버전의 데이터베이스 엔진에는 64 GB의 메모리 용량이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbc71-115">In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], the database engine in the Standard edition had a memory capacity of 64 GB.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbc71-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fbc71-116">See Also</span></span>  
 <span data-ttu-id="fbc71-117">[SQL Server 2014의 새로운 기능](../what-s-new-in-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="fbc71-117">[What's New in SQL Server 2014](../what-s-new-in-sql-server-2016.md) </span></span>  
 <span data-ttu-id="fbc71-118">[SQL Server 2014에 대 한 제품 사양](../../../2014/getting-started/sql-server-2014-product-specifications.md) </span><span class="sxs-lookup"><span data-stu-id="fbc71-118">[Product Specifications for SQL Server 2014](../../../2014/getting-started/sql-server-2014-product-specifications.md) </span></span>  
 <span data-ttu-id="fbc71-119">[SQL Server 설치 계획](../../../2014/sql-server/install/planning-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="fbc71-119">[Planning a SQL Server Installation](../../../2014/sql-server/install/planning-a-sql-server-installation.md) </span></span>  
 [<span data-ttu-id="fbc71-120">SQL Server 2014 설치에 대한 하드웨어 및 소프트웨어 요구 사항</span><span class="sxs-lookup"><span data-stu-id="fbc71-120">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](hardware-and-software-requirements-for-installing-sql-server.md)  
  
  
