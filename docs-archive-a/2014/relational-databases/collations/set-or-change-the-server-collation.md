---
title: 서버 데이터 정렬 설정 또는 변경 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- server collations [SQL Server]
- collations [SQL Server], server
ms.assetid: 3242deef-6f5f-4051-a121-36b3b4da851d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 35e7be051c8cf63a272f2bf42fb54b1c45ed4160
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661159"
---
# <a name="set-or-change-the-server-collation"></a><span data-ttu-id="05973-102">서버 데이터 정렬 설정 또는 변경</span><span class="sxs-lookup"><span data-stu-id="05973-102">Set or Change the Server Collation</span></span>
  <span data-ttu-id="05973-103">서버 데이터 정렬은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 설치된 모든 시스템 데이터베이스와 새로 만든 사용자 데이터베이스의 기본 데이터 정렬로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="05973-103">The server collation acts as the default collation for all system databases that are installed with the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and also any newly created user databases.</span></span> <span data-ttu-id="05973-104">서버 데이터 정렬은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 과정에서 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="05973-104">The server collation is specified during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="05973-105">자세한 내용은 [Collation and Unicode Support](collation-and-unicode-support.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05973-105">For more information, see [Collation and Unicode Support](collation-and-unicode-support.md).</span></span>  
  
## <a name="changing-the-server-collation"></a><span data-ttu-id="05973-106">서버 데이터 정렬 변경</span><span class="sxs-lookup"><span data-stu-id="05973-106">Changing the Server Collation</span></span>  
 <span data-ttu-id="05973-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 기본 데이터 정렬을 변경하는 작업은 복잡할 수 있으며 다음과 같은 단계가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="05973-107">Changing the default collation for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be a complex operation and involves the following steps:</span></span>  
  
-   <span data-ttu-id="05973-108">사용자 데이터베이스와 그 안의 모든 개체를 다시 만드는 데 필요한 정보나 스크립트가 모두 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="05973-108">Make sure you have all the information or scripts needed to re-create your user databases and all the objects in them.</span></span>  
  
-   <span data-ttu-id="05973-109">[bcp Utility](../../tools/bcp-utility.md)등의 도구를 사용하여 모든 데이터를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="05973-109">Export all your data using a tool such as the [bcp Utility](../../tools/bcp-utility.md).</span></span> <span data-ttu-id="05973-110">자세한 내용은 [데이터 대량 가져오기 및 내보내기&#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05973-110">For more information, see [Bulk Import and Export of Data &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md).</span></span>  
  
-   <span data-ttu-id="05973-111">모든 사용자 데이터베이스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="05973-111">Drop all the user databases.</span></span>  
  
-   <span data-ttu-id="05973-112">**setup** 명령의 SQLCOLLATION 속성에 새 데이터 정렬을 지정하여 master 데이터베이스를 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="05973-112">Rebuild the master database specifying the new collation in the SQLCOLLATION property of the **setup** command.</span></span> <span data-ttu-id="05973-113">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="05973-113">For example:</span></span>  
  
    ```  
    Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName   
    /SQLSYSADMINACCOUNTS=accounts /[ SAPWD= StrongPassword ]   
    /SQLCOLLATION=CollationName  
    ```  
  
     <span data-ttu-id="05973-114">자세한 내용은 [시스템 데이터베이스 다시 작성](../databases/system-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05973-114">For more information, see [Rebuild System Databases](../databases/system-databases.md).</span></span>  
  
-   <span data-ttu-id="05973-115">모든 데이터베이스와 그 안의 모든 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="05973-115">Create all the databases and all the objects in them.</span></span>  
  
-   <span data-ttu-id="05973-116">모든 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="05973-116">Import all your data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="05973-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 기본 데이터 정렬을 변경하는 대신 사용자가 만드는 각각의 새 데이터베이스에 대해 기본 데이터 정렬을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05973-117">Instead of changing the default collation of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can specify a default collation for each new database you create.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05973-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="05973-118">See Also</span></span>  
 <span data-ttu-id="05973-119">[데이터 정렬 및 유니코드 지원](collation-and-unicode-support.md) </span><span class="sxs-lookup"><span data-stu-id="05973-119">[Collation and Unicode Support](collation-and-unicode-support.md) </span></span>  
 <span data-ttu-id="05973-120">[데이터베이스 데이터 정렬 설정 또는 변경](set-or-change-the-database-collation.md) </span><span class="sxs-lookup"><span data-stu-id="05973-120">[Set or Change the Database Collation](set-or-change-the-database-collation.md) </span></span>  
 <span data-ttu-id="05973-121">[열 데이터 정렬 설정 또는 변경](set-or-change-the-column-collation.md) </span><span class="sxs-lookup"><span data-stu-id="05973-121">[Set or Change the Column Collation](set-or-change-the-column-collation.md) </span></span>  
 [<span data-ttu-id="05973-122">시스템 데이터베이스 다시 작성</span><span class="sxs-lookup"><span data-stu-id="05973-122">Rebuild System Databases</span></span>](../databases/system-databases.md)  
  
  
