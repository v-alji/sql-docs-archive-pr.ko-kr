---
title: 구성 관리용 WMI 공급자 이해 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management, operations supported
ms.assetid: 92323972-7943-4208-bbf4-050774fb6027
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0f4f38265093fdb0c27d6bd49ff64ba4b572111e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638570"
---
# <a name="understanding-the-wmi-provider-for-configuration-management"></a><span data-ttu-id="b7455-102">구성 관리용 WMI 공급자 이해</span><span class="sxs-lookup"><span data-stu-id="b7455-102">Understanding the WMI Provider for Configuration Management</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="b7455-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]구성 관리용 WMI 공급자를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7455-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides the WMI Provider for Configuration Management.</span></span> <span data-ttu-id="b7455-104">구성 관리용 WMI 공급자는 WMI(Windows Management Instrumentation)를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 클라이언트/서버 네트워크 설정 및 서버 별칭을 관리할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7455-104">This lets you use Windows Management Instrumentation (WMI) to manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client and server network settings, and server aliases.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="b7455-105">서비스, 네트워크 설정 및 별칭은 컴퓨터의 root\Microsoft\SqlServer\ComputerManagement*nn* 네임 스페이스에 있는 WMI 개체로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7455-105">services, network settings, and aliases are represented by WMI objects in the root\Microsoft\SqlServer\ComputerManagement*nn* namespace of the computer.</span></span> <span data-ttu-id="b7455-106">지정된 컴퓨터에서 WMI 공급자를 사용하여 연결이 설정된 후에는 WQL이나 스크립팅 언어를 사용하여 서비스, 네트워크 설정 및 별칭을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7455-106">After a connection is established with the WMI provider on the specified computer, the services, network settings, and aliases can be queried using WQL or a scripting language.</span></span>  
  
 <span data-ttu-id="b7455-107">WMI 공급자는 인스턴스 공급자로서</span><span class="sxs-lookup"><span data-stu-id="b7455-107">The WMI Provider is an instance provider.</span></span> <span data-ttu-id="b7455-108">[WMI 클래스](../wmi-provider-configuration-classes/wmi-provider-for-configuration-management-classes.md) 의 인스턴스를 제공 하 고 다음과 같은 비동기 작업을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7455-108">It supplies instances of the [WMI Classes](../wmi-provider-configuration-classes/wmi-provider-for-configuration-management-classes.md) and supports the following asynchronous operations.</span></span>  
  
 <span data-ttu-id="b7455-109">인스턴스 검색</span><span class="sxs-lookup"><span data-stu-id="b7455-109">Instance retrieval</span></span>  
 <span data-ttu-id="b7455-110">특정 클래스 유형 인스턴스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="b7455-110">Retrieval of a particular class type instance.</span></span>  
  
 <span data-ttu-id="b7455-111">열거형</span><span class="sxs-lookup"><span data-stu-id="b7455-111">Enumeration</span></span>  
 <span data-ttu-id="b7455-112">모든 클래스 유형 인스턴스를 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="b7455-112">Enumeration of all instances of a class type.</span></span>  
  
 <span data-ttu-id="b7455-113">수정</span><span class="sxs-lookup"><span data-stu-id="b7455-113">Modification</span></span>  
 <span data-ttu-id="b7455-114">특정 클래스 유형 인스턴스를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="b7455-114">Modification of a particular instance of a class type.</span></span>  
  
 <span data-ttu-id="b7455-115">클래스에는 해당 속성을 수정할 수 있는 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7455-115">Classes have methods that allow the modification of their properties.</span></span>  
  
 <span data-ttu-id="b7455-116">삭제</span><span class="sxs-lookup"><span data-stu-id="b7455-116">Deletion</span></span>  
 <span data-ttu-id="b7455-117">특정 클래스 유형 인스턴스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="b7455-117">Removing a particular instance of a class type.</span></span>  
  
 <span data-ttu-id="b7455-118">쿼리 처리</span><span class="sxs-lookup"><span data-stu-id="b7455-118">Query processing</span></span>  
 <span data-ttu-id="b7455-119">필터를 기반으로 클래스 유형 인스턴스를 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="b7455-119">Enumeration of instances of a class type based on a filter.</span></span>  
  
 <span data-ttu-id="b7455-120">구성 관리용 WMI 공급자를 사용 하는 관리 응용 프로그램의 예는 [구성 관리용 Wmi 공급자에 WQL 및 스크립트 언어 사용](using-wql-and-scripting-languages-with-the-wmi-provider.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b7455-120">For examples of management application using the WMI Provider for Configuration Management, see [Using WQL and Scripting Languages with the WMI Provider for Configuration Management](using-wql-and-scripting-languages-with-the-wmi-provider.md).</span></span>  
  
 <span data-ttu-id="b7455-121">WMI 공급자를 사용 하 여 관리 응용 프로그램을 프로그래밍 하는 방법에 대 한 자세한 내용은 .NET Framework SDK의 WMI 설명서를 참조 하십시오 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b7455-121">For more information about programming management applications using the WMI Provider, see the WMI documentation in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework SDK.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7455-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b7455-122">See Also</span></span>  
 <span data-ttu-id="b7455-123">[구성 관리용 WMI 공급자 작업](working-with-the-wmi-provider-for-configuration-management.md) </span><span class="sxs-lookup"><span data-stu-id="b7455-123">[Working with the WMI Provider for Configuration Management](working-with-the-wmi-provider-for-configuration-management.md) </span></span>  
 [<span data-ttu-id="b7455-124">구성 관리용 WMI 공급자에 WQL 및 스크립트 언어 사용</span><span class="sxs-lookup"><span data-stu-id="b7455-124">Using WQL and Scripting Languages with the WMI Provider for Configuration Management</span></span>](using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  
