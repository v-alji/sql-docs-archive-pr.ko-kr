---
title: CLR 통합 어셈블리 관리 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- database objects [CLR integration], assemblies
- common language runtime [SQL Server], assemblies
- assemblies [CLR integration], managing
ms.assetid: bdbbf325-14f6-460e-a35a-d3861d3c961e
author: rothja
ms.author: jroth
ms.openlocfilehash: 191ccd73ca42ef4c26291e6de88f5f2b0cf565ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735324"
---
# <a name="managing-clr-integration-assemblies"></a><span data-ttu-id="80a38-102">CLR 통합 어셈블리 관리</span><span class="sxs-lookup"><span data-stu-id="80a38-102">Managing CLR Integration Assemblies</span></span>
  <span data-ttu-id="80a38-103">관리 코드는 컴파일한 다음 어셈블리라는 단위로 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="80a38-103">Managed code is compiled and then deployed in units called an assembly.</span></span> <span data-ttu-id="80a38-104">어셈블리는 DLL이나 실행 파일(.exe)로 패키지됩니다.</span><span class="sxs-lookup"><span data-stu-id="80a38-104">An assembly is packaged as a DLL or executable (.exe) file.</span></span> <span data-ttu-id="80a38-105">실행 파일은 독립적으로 실행할 수 있는 반면 DLL은 기존 애플리케이션 내에서 호스팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80a38-105">While an executable file can run on its own, a DLL must be hosted in an existing application.</span></span> <span data-ttu-id="80a38-106">관리 되는 DLL 어셈블리를에 로드 하 여 호스팅할 수 있습니다 [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="80a38-106">Managed DLL assemblies can be loaded into and hosted by [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)].</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="80a38-107">CREATE ASSEMBLY 문을 사용 하는 데이터베이스는 프로세스에서 로드 하 고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80a38-107">database using the CREATE ASSEMBLY statement, before it can be loaded in the process and used.</span></span> <span data-ttu-id="80a38-108">ALTER ASSEMBLY 문을 사용하여 어셈블리를 최신 버전에서 업데이트하거나 DROP ASSEMBLY 문을 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 제거할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80a38-108">Assemblies can also be updated from a more recent version using the ALTER ASSEMBLY statement, or removed from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] using the DROP ASSEMBLY statement.</span></span>  
  
 <span data-ttu-id="80a38-109">어셈블리 정보는 어셈블리가 설치된 데이터베이스의 `sys.assembly_files` 테이블에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="80a38-109">Assembly information is stored in the `sys.assembly_files` table in the database where the assembly has been installed.</span></span> <span data-ttu-id="80a38-110">`sys.assembly_files` 테이블에는 다음 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80a38-110">The `sys.assembly_files` table contains the following columns.</span></span>  
  
|<span data-ttu-id="80a38-111">열</span><span class="sxs-lookup"><span data-stu-id="80a38-111">Column</span></span>|<span data-ttu-id="80a38-112">Description</span><span class="sxs-lookup"><span data-stu-id="80a38-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="80a38-113">assembly_id</span><span class="sxs-lookup"><span data-stu-id="80a38-113">assembly_id</span></span>|<span data-ttu-id="80a38-114">어셈블리에 대해 정의되는 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="80a38-114">The identifier defined for the assembly.</span></span> <span data-ttu-id="80a38-115">해당 어셈블리와 관련한 모든 개체에 이 번호가 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="80a38-115">This number is assigned to all objects relating to the same assembly.</span></span>|  
|<span data-ttu-id="80a38-116">name</span><span class="sxs-lookup"><span data-stu-id="80a38-116">name</span></span>|<span data-ttu-id="80a38-117">개체의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="80a38-117">The name of the object.</span></span>|  
|<span data-ttu-id="80a38-118">file_id</span><span class="sxs-lookup"><span data-stu-id="80a38-118">file_id</span></span>|<span data-ttu-id="80a38-119">각 개체를 식별하는 번호이며 `assembly_id`와 연결된 첫 번째 개체에 값 1이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="80a38-119">A number identifying each object, with the first object associated with a given `assembly_id` being given the value of 1.</span></span> <span data-ttu-id="80a38-120">같은 `assembly_id`에 연결된 개체가 여러 개 있으면 차례로 1씩 증가한 `file_id` 값이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="80a38-120">If multiple objects are associated with the same `assembly_id`, then each subsequent `file_id` value is incremented by 1.</span></span>|  
|<span data-ttu-id="80a38-121">콘텐츠</span><span class="sxs-lookup"><span data-stu-id="80a38-121">content</span></span>|<span data-ttu-id="80a38-122">어셈블리 또는 파일의 16진수 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="80a38-122">The hexadecimal representation of the assembly or file.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="80a38-123">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="80a38-123">In This Section</span></span>  
 [<span data-ttu-id="80a38-124">어셈블리 만들기</span><span class="sxs-lookup"><span data-stu-id="80a38-124">Creating an Assembly</span></span>](creating-an-assembly.md)  
 <span data-ttu-id="80a38-125">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 SAFE, EXTERNAL_ACCESS 및 UNSAFE CLR 어셈블리를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="80a38-125">Discusses creating SAFE, EXTERNAL_ACCESS, and UNSAFE CLR assemblies in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="80a38-126">어셈블리 변경</span><span class="sxs-lookup"><span data-stu-id="80a38-126">Altering an Assembly</span></span>](altering-an-assembly.md)  
 <span data-ttu-id="80a38-127">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 CLR 어셈블리를 업데이트하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="80a38-127">Describes updating CLR assemblies in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="80a38-128">어셈블리 삭제</span><span class="sxs-lookup"><span data-stu-id="80a38-128">Dropping an Assembly</span></span>](dropping-an-assembly.md)  
 <span data-ttu-id="80a38-129">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 CLR 어셈블리를 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="80a38-129">Discusses dropping CLR assemblies from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80a38-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="80a38-130">See Also</span></span>  
 <span data-ttu-id="80a38-131">[CLR 통합 보안](../security/clr-integration-security.md) </span><span class="sxs-lookup"><span data-stu-id="80a38-131">[CLR Integration Security](../security/clr-integration-security.md) </span></span>  
 [<span data-ttu-id="80a38-132">CLR 통합 코드 액세스 보안</span><span class="sxs-lookup"><span data-stu-id="80a38-132">CLR Integration Code Access Security</span></span>](../security/clr-integration-code-access-security.md)  
  
  
