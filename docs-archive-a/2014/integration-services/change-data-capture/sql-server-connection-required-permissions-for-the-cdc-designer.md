---
title: SQL Server 연결을 위해 CDC Designer에 대해 필요한 권한 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 80334de2-17c1-43c9-951e-21a9f864e9cb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0815a5d8f1cb66dee0d290a45166ebb395c8efa8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646576"
---
# <a name="sql-server-connection-required-permissions-for-the-cdc-designer"></a><span data-ttu-id="5c8f6-102">SQL Server 연결을 위해 CDC Designer에 대해 필요한 권한</span><span class="sxs-lookup"><span data-stu-id="5c8f6-102">SQL Server Connection Required Permissions for the CDC Designer</span></span>
  <span data-ttu-id="5c8f6-103">CDC Designer 콘솔에서 태스크를 수행하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결 정보가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-103">The CDC Designer Console requires connection information to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to perform its tasks.</span></span> <span data-ttu-id="5c8f6-104">이 항목에서는 **연결 설정을 위해** SQL Server에 연결 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]대화 상자에서 지정할 수 있는 정보에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-104">This topic describes the information that can be provided in the **Connect to SQL Server** dialog box for setting up the connection to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="5c8f6-105">**연결 정보를 사용할 수 없거나 정보가 있지만 연결에 필요한 권한이 없는 경우와 같이 필요한 경우** SQL Server에 연결 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-105">The **Connect to SQL Server** dialog box opens when necessary, such as when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection information is not available or when the information exists but the connection does not have the required permissions.</span></span>  
  
 <span data-ttu-id="5c8f6-106">다음 표에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결이 필요한 다양한 태스크와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인/사용자의 필요한 권한에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5c8f6-106">The following table describes the various tasks where a connection to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is required and the required permissions from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login/user.</span></span>  
  
|<span data-ttu-id="5c8f6-107">Task</span><span class="sxs-lookup"><span data-stu-id="5c8f6-107">Task</span></span>|<span data-ttu-id="5c8f6-108">최소 권한</span><span class="sxs-lookup"><span data-stu-id="5c8f6-108">Minimum Permissions</span></span>|  
|----------|-------------------------|  
|<span data-ttu-id="5c8f6-109">연관된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 사용하여 CDC Service 및 인스턴스 목록 보기</span><span class="sxs-lookup"><span data-stu-id="5c8f6-109">View the list of CDC Services and Instances using the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>|<span data-ttu-id="5c8f6-110">`db_datareader` 역할</span><span class="sxs-lookup"><span data-stu-id="5c8f6-110">`db_datareader` role on MSXDBCDC</span></span>|  
|<span data-ttu-id="5c8f6-111">CDC 인스턴스 시작/중지</span><span class="sxs-lookup"><span data-stu-id="5c8f6-111">Start/Stop CDC Instance(s)</span></span>|<span data-ttu-id="5c8f6-112">`db_datareader` 및 `db_datawriter` 역할</span><span class="sxs-lookup"><span data-stu-id="5c8f6-112">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span>|  
|<span data-ttu-id="5c8f6-113">CDC 인스턴스 상태 보기</span><span class="sxs-lookup"><span data-stu-id="5c8f6-113">View the CDC Instance status.</span></span>|<span data-ttu-id="5c8f6-114">`db_owner` 역할</span><span class="sxs-lookup"><span data-stu-id="5c8f6-114">`db_owner` role on the CDC Instance database</span></span>|  
|<span data-ttu-id="5c8f6-115">새 Oracle CDC 인스턴스 데이터베이스 만들기</span><span class="sxs-lookup"><span data-stu-id="5c8f6-115">Create a new Oracle CDC Instance database.</span></span>|<span data-ttu-id="5c8f6-116">`dbcreator` 고정 서버 역할</span><span class="sxs-lookup"><span data-stu-id="5c8f6-116">`dbcreator` fixed-server role</span></span>|  
|<span data-ttu-id="5c8f6-117">새 Oracle CDC 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="5c8f6-117">Create a new Oracle CDC Instance.</span></span>|<span data-ttu-id="5c8f6-118">`db_datareader` 역할</span><span class="sxs-lookup"><span data-stu-id="5c8f6-118">`db_datareader` role on MSXDBCDC</span></span><br /><br /> <span data-ttu-id="5c8f6-119">`db_owner` 역할</span><span class="sxs-lookup"><span data-stu-id="5c8f6-119">`db_owner` role on the CDC database that was created.</span></span>|  
|<span data-ttu-id="5c8f6-120">배포 스크립트 가져오기</span><span class="sxs-lookup"><span data-stu-id="5c8f6-120">Get deployment scripts.</span></span>|<span data-ttu-id="5c8f6-121">`db_datareader` 및 `db_datawriter` 역할</span><span class="sxs-lookup"><span data-stu-id="5c8f6-121">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span><br /><br /> <span data-ttu-id="5c8f6-122">`db_owner` 역할</span><span class="sxs-lookup"><span data-stu-id="5c8f6-122">`db_owner` role on the relatedCDC database</span></span>|  
|<span data-ttu-id="5c8f6-123">구성 변경 및 캡처 인스턴스 추가/제거</span><span class="sxs-lookup"><span data-stu-id="5c8f6-123">Change configuration and add/remove capture instances.</span></span>|<span data-ttu-id="5c8f6-124">`db_datareader` 및 `db_datawriter` 역할</span><span class="sxs-lookup"><span data-stu-id="5c8f6-124">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span><br /><br /> <span data-ttu-id="5c8f6-125">`db_owner` 역할</span><span class="sxs-lookup"><span data-stu-id="5c8f6-125">`db_owner` role on the related CDC database</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c8f6-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5c8f6-126">See Also</span></span>  
 <span data-ttu-id="5c8f6-127">[CDC Designer 콘솔 액세스](access-the-cdc-designer-console.md) </span><span class="sxs-lookup"><span data-stu-id="5c8f6-127">[Access the CDC Designer Console](access-the-cdc-designer-console.md) </span></span>  
 [<span data-ttu-id="5c8f6-128">인스턴스를 만들기 위한 SQL Server 연결</span><span class="sxs-lookup"><span data-stu-id="5c8f6-128">SQL Server Connection for Instance Creation</span></span>](sql-server-connection-for-instance-creation.md)  
  
  
